# 📝 Exemplos Práticos de Código MongoDB
## Material Complementar para Slides - Comparações SQL vs MongoDB

---

## EXEMPLOS PARA SLIDE 6: NoSQL vs SQL

### Exemplo 1: Criar e Inserir Cliente

#### SQL (Relacional)
```sql
-- 1. Criar tabela (schema fixo)
CREATE TABLE CLIENTES (
    id INT PRIMARY KEY AUTO_INCREMENT,
    nome VARCHAR(255) NOT NULL,
    email VARCHAR(255) NOT NULL,
    cpf VARCHAR(14) UNIQUE,
    data_cadastro DATETIME DEFAULT CURRENT_TIMESTAMP
);

-- 2. Criar tabela de endereços (separada!)
CREATE TABLE ENDERECO (
    id INT PRIMARY KEY AUTO_INCREMENT,
    cliente_id INT NOT NULL,
    rua VARCHAR(255),
    numero INT,
    cidade VARCHAR(100),
    FOREIGN KEY (cliente_id) REFERENCES CLIENTES(id)
);

-- 3. Inserir dados (em múltiplas tabelas)
INSERT INTO CLIENTES (nome, email, cpf)
VALUES ('João Silva', 'joao@email.com', '123.456.789-00');

INSERT INTO ENDERECO (cliente_id, rua, numero, cidade)
VALUES (1, 'Rua A', 123, 'São Paulo');

-- 4. Para recuperar tudo, precisa de JOIN
SELECT c.*, e.rua, e.numero, e.cidade
FROM CLIENTES c
LEFT JOIN ENDERECO e ON c.id = e.cliente_id
WHERE c.cpf = '123.456.789-00';
```

**Problemas SQL:**
- ❌ Schema fixo: se quiser adicionar novo campo (telefone), ALTER TABLE
- ❌ Dados espalhados: cliente + endereço em 2 tabelas
- ❌ Precisa JOIN: mais complexo, mais lento em escala

#### MongoDB (Documento)
```javascript
// 1. Nenhuma criação de schema necessária
// 2. Inserir documento completo (tudo junto)
db.clientes.insertOne({
  _id: ObjectId("507f1f77bcf86cd799439011"),
  nome: "João Silva",
  email: "joao@email.com",
  cpf: "123.456.789-00",
  data_cadastro: new Date(),
  endereco: {
    rua: "Rua A",
    numero: 123,
    cidade: "São Paulo"
  }
})

// 3. Para recuperar, query simples
db.clientes.findOne({ cpf: "123.456.789-00" })

// 4. Resultado: documento completo com tudo aninhado
{
  "_id": ObjectId("507f1f77bcf86cd799439011"),
  "nome": "João Silva",
  "email": "joao@email.com",
  "cpf": "123.456.789-00",
  "data_cadastro": ISODate("2024-01-15T10:30:00Z"),
  "endereco": {
    "rua": "Rua A",
    "numero": 123,
    "cidade": "São Paulo"
  }
}
```

**Vantagens MongoDB:**
- ✅ Nenhuma schema: adiciona campos conforme precisa
- ✅ Dados juntos: tudo em 1 documento
- ✅ Query simples: sem JOINs
- ✅ Pronto para uso: aplicação obtém objeto completo

---

### Exemplo 2: Evolução de Schema (O Diferencial MongoDB)

#### SQL - Adicionar campo
```sql
-- Problema: ALTER TABLE é operação cara em produção
ALTER TABLE CLIENTES ADD COLUMN telefone VARCHAR(20);

-- Em banco com 100 milhões de registros:
-- - Leva minutos
-- - Lock na tabela (ninguém consegue acessar)
-- - Pode causar downtime
```

#### MongoDB - Adicionar campo
```javascript
// Nenhuma operação necessária!
// Simplesmente insira um novo documento com o campo novo

db.clientes.insertOne({
  nome: "Maria Silva",
  email: "maria@email.com",
  cpf: "987.654.321-00",
  telefone: "11999999999",  // Campo novo
  endereco: { ... }
})

// Documentos antigos continuam sem telefone
// Aplicação trata como campo opcional
// ZERO downtime, ZERO lock, ZERO problema
```

---

## EXEMPLOS PARA SLIDE 11-14: CRUD Detalhado

### Exemplo Completo: Sistema de Conta Bancária

```javascript
// ============================================
// CREATE - Inserir Nova Conta
// ============================================

db.contas.insertOne({
  _id: ObjectId("507f1f77bcf86cd799439011"),
  numero_conta: "12345-6",
  agencia: "0001",
  cliente_id: ObjectId("507f1f77bcf86cd799439010"),
  tipo: "corrente",
  saldo: Decimal128("5000.00"),
  status: "ativa",
  data_criacao: new Date("2024-01-15"),
  historico_saldos: [
    { data: new Date("2024-01-15"), saldo: Decimal128("5000.00") }
  ]
})

// ============================================
// READ - Consultar Contas
// ============================================

// 1. Busca simples
db.contas.findOne({ numero_conta: "12345-6" })

// 2. Busca com múltiplos filtros
db.contas.find({
  cliente_id: ObjectId("507f1f77bcf86cd799439010"),
  status: "ativa"
})

// 3. Contas com saldo > 5000
db.contas.find({
  saldo: { $gte: Decimal128("5000.00") }
}).sort({ saldo: -1 })

// 4. Contas criadas nos últimos 30 dias
db.contas.find({
  data_criacao: {
    $gte: new Date(new Date().setDate(new Date().getDate() - 30))
  }
})

// 5. Contas de um cliente específico com projeção
db.contas.find(
  { cliente_id: ObjectId("507f1f77bcf86cd799439010") },
  { numero_conta: 1, saldo: 1, _id: 0 }
)

// ============================================
// UPDATE - Modificar Contas
// ============================================

// 1. Saque: decrementar saldo (OPERAÇÃO ATÔMICA)
db.contas.updateOne(
  { _id: ObjectId("507f1f77bcf86cd799439011") },
  {
    $inc: { saldo: Decimal128("-500.00") },
    $set: { atualizado_em: new Date() }
  }
)
// Resultado: saldo vai de 5000 para 4500

// 2. Deposito: incrementar saldo
db.contas.updateOne(
  { numero_conta: "12345-6" },
  { $inc: { saldo: Decimal128("1000.00") } }
)

// 3. Fechar conta (soft delete)
db.contas.updateOne(
  { _id: ObjectId("507f1f77bcf86cd799439011") },
  {
    $set: {
      status: "fechada",
      data_fechamento: new Date(),
      fechada_por: "gerente_001"
    }
  }
)

// 4. Adicionar ao histórico de saldos
db.contas.updateOne(
  { _id: ObjectId("507f1f77bcf86cd799439011") },
  {
    $push: {
      historico_saldos: {
        data: new Date(),
        saldo: Decimal128("4500.00")
      }
    }
  }
)

// ============================================
// DELETE - Remover Contas
// ============================================

// ❌ NÃO FAÇA EM PRODUÇÃO (irrecuperável)
db.contas.deleteOne({ _id: ObjectId("507f1f77bcf86cd799439011") })

// ✅ FAÇA ASSIM: Soft Delete
db.contas.updateOne(
  { _id: ObjectId("507f1f77bcf86cd799439011") },
  {
    $set: {
      deletado: true,
      deletado_em: new Date(),
      deletado_por: "admin_001"
    }
  }
)

// Depois, suas queries filtram por deletado: false
db.contas.find({ deletado: { $ne: true } })
```

---

## EXEMPLOS PARA SLIDE 15-16: Operadores

### Tabela de Comparação: Operadores SQL vs MongoDB

| Operação | SQL | MongoDB |
|----------|-----|---------|
| Igual | `WHERE saldo = 5000` | `.find({ saldo: 5000 })` ou `.find({ saldo: { $eq: 5000 } })` |
| Maior | `WHERE saldo > 5000` | `.find({ saldo: { $gt: 5000 } })` |
| Maior ou igual | `WHERE saldo >= 5000` | `.find({ saldo: { $gte: 5000 } })` |
| Menor | `WHERE saldo < 1000` | `.find({ saldo: { $lt: 1000 } })` |
| Não igual | `WHERE status <> 'ativa'` | `.find({ status: { $ne: "ativa" } })` |
| Em lista | `WHERE status IN ('ativa', 'premium')` | `.find({ status: { $in: ["ativa", "premium"] } })` |
| AND (E) | `WHERE saldo > 1000 AND status = 'ativa'` | `.find({ saldo: { $gt: 1000 }, status: "ativa" })` |
| OR (OU) | `WHERE saldo > 100000 OR premium = true` | `.find({ $or: [ { saldo: { $gt: 100000 } }, { premium: true } ] })` |
| Campo existe | `WHERE telefone IS NOT NULL` | `.find({ telefone: { $exists: true } })` |
| Tipo de dado | Não aplicável | `.find({ saldo: { $type: "decimal" } })` |

### Exemplos Práticos de Operadores

```javascript
// ============================================
// COMPARAÇÃO
// ============================================

// Clientes com saldo entre 5000 e 10000
db.clientes.find({
  saldo: { $gte: Decimal128("5000"), $lte: Decimal128("10000") }
})

// Contas criadas em 2024
db.contas.find({
  data_criacao: {
    $gte: new Date("2024-01-01"),
    $lt: new Date("2025-01-01")
  }
})

// ============================================
// LÓGICA
// ============================================

// Clientes VIP: saldo alto OU status premium
db.clientes.find({
  $or: [
    { saldo: { $gte: Decimal128("100000") } },
    { status: "premium" }
  ]
})

// Clientes NÃO vip
db.clientes.find({
  $nor: [
    { saldo: { $gte: Decimal128("100000") } },
    { status: "premium" }
  ]
})

// Clientes ativos que NÃO têm mais de 100 transações
db.clientes.find({
  ativo: true,
  numero_transacoes: { $not: { $gt: 100 } }
})

// ============================================
// ARRAY
// ============================================

// Clientes que têm uma conta ativa com saldo > 5000
db.clientes.find({
  contas: {
    $elemMatch: {
      status: "ativa",
      saldo: { $gt: Decimal128("5000") }
    }
  }
})

// Clientes que têm CPF registrado (array não vazio)
db.clientes.find({
  cpf_anteriores: { $not: { $size: 0 } }
})

// ============================================
// STRING (REGEX)
// ============================================

// Clientes com nome contendo "Silva" (case insensitive)
db.clientes.find({
  nome: { $regex: "silva", $options: "i" }
})

// Clientes com email que termina em @gmail.com
db.clientes.find({
  email: { $regex: "@gmail\.com$", $options: "i" }
})

// ============================================
// EXISTÊNCIA
// ============================================

// Clientes que têm email cadastrado
db.clientes.find({ email: { $exists: true } })

// Clientes que NÃO têm telefone (campo não existe)
db.clientes.find({ telefone: { $exists: false } })

// Documentos onde saldo é null
db.clientes.find({ saldo: null })
```

---

## EXEMPLOS PARA SLIDE 17: Aggregation Pipeline

### Cenário Real: Relatório de Transações Bancárias

```javascript
// ============================================
// Agregação 1: Top 10 Clientes por Volume
// ============================================

db.transacoes.aggregate([
  // Stage 1: Filtrar transações confirmadas do último mês
  {
    $match: {
      status: "confirmado",
      data: {
        $gte: new Date(new Date().setDate(new Date().getDate() - 30))
      }
    }
  },

  // Stage 2: Agrupar por cliente e calcular totais
  {
    $group: {
      _id: "$cliente_id",
      total_movimentado: { $sum: "$valor" },
      numero_transacoes: { $sum: 1 },
      maior_transacao: { $max: "$valor" },
      menor_transacao: { $min: "$valor" },
      media_transacao: { $avg: "$valor" }
    }
  },

  // Stage 3: Ordenar por volume descrescente
  { $sort: { total_movimentado: -1 } },

  // Stage 4: Pegar apenas top 10
  { $limit: 10 },

  // Stage 5: Trazer dados do cliente (JOIN)
  {
    $lookup: {
      from: "clientes",
      localField: "_id",
      foreignField: "_id",
      as: "cliente"
    }
  },

  // Stage 6: Desempacotar array (pegar primeiro elemento)
  { $unwind: "$cliente" },

  // Stage 7: Projetar apenas campos desejados
  {
    $project: {
      _id: 0,
      cliente_id: "$_id",
      nome_cliente: "$cliente.nome",
      total_movimentado: 1,
      numero_transacoes: 1,
      media_transacao: 1,
      maior_transacao: 1
    }
  }
])

// Resultado esperado:
/*
[
  {
    "cliente_id": ObjectId("..."),
    "nome_cliente": "João Silva",
    "total_movimentado": Decimal128("150000.00"),
    "numero_transacoes": 25,
    "media_transacao": Decimal128("6000.00"),
    "maior_transacao": Decimal128("15000.00")
  },
  {
    "cliente_id": ObjectId("..."),
    "nome_cliente": "Maria Santos",
    "total_movimentado": Decimal128("120000.00"),
    "numero_transacoes": 18,
    "media_transacao": Decimal128("6666.67"),
    "maior_transacao": Decimal128("20000.00")
  }
  // ... mais 8 clientes
]
*/

// ============================================
// Agregação 2: Distribuição de Saldo por Status
// ============================================

db.clientes.aggregate([
  // Agrupar por status e contar
  {
    $group: {
      _id: "$status",
      numero_clientes: { $sum: 1 },
      saldo_total: { $sum: "$saldo" },
      saldo_medio: { $avg: "$saldo" },
      saldo_maximo: { $max: "$saldo" },
      saldo_minimo: { $min: "$saldo" }
    }
  },

  // Ordenar por número de clientes
  { $sort: { numero_clientes: -1 } }
])

// Resultado:
/*
[
  {
    "_id": "ativo",
    "numero_clientes": 8500,
    "saldo_total": Decimal128("50000000.00"),
    "saldo_medio": Decimal128("5882.35"),
    "saldo_maximo": Decimal128("500000.00"),
    "saldo_minimo": Decimal128("100.00")
  },
  {
    "_id": "premium",
    "numero_clientes": 1200,
    "saldo_total": Decimal128("25000000.00"),
    "saldo_medio": Decimal128("20833.33"),
    "saldo_maximo": Decimal128("1000000.00"),
    "saldo_minimo": Decimal128("50000.00")
  },
  // ...
]
*/

// ============================================
// Agregação 3: Análise de Fraude (COMPLEXA)
// ============================================

db.transacoes.aggregate([
  // Filtrar últimas 24 horas
  {
    $match: {
      data: {
        $gte: new Date(new Date().setHours(new Date().getHours() - 24))
      }
    }
  },

  // Agrupar por cliente
  {
    $group: {
      _id: "$cliente_id",
      transacoes: { $push: "$$ROOT" },  // Manter todas as transações
      numero_transacoes: { $sum: 1 },
      volume_total: { $sum: "$valor" },
      maior_transacao: { $max: "$valor" },
      paises: { $addToSet: "$destino.pais" }
    }
  },

  // Filtrar clientes suspeitos
  {
    $match: {
      $expr: {
        $or: [
          { $gt: ["$numero_transacoes", 50] },           // 50+ transações/dia
          { $gte: ["$volume_total", Decimal128("100000")] },  // 100k+ volume
          { $gte: [{ $size: "$paises" }, 5] }            // 5+ países diferentes
        ]
      }
    }
  },

  // Adicionar score de risco
  {
    $addFields: {
      score_risco: {
        $add: [
          { $cond: [{ $gt: ["$numero_transacoes", 50] }, 0.3, 0] },
          { $cond: [{ $gte: ["$volume_total", Decimal128("100000")] }, 0.4, 0] },
          { $cond: [{ $gte: [{ $size: "$paises" }, 5] }, 0.3, 0] }
        ]
      }
    }
  },

  // Ordenar por risco (maior primeiro)
  { $sort: { score_risco: -1 } },

  // Top 50 suspeitos
  { $limit: 50 }
])
```

---

## EXEMPLOS PARA SLIDE 18-19: Índices

### Comparação de Performance: Com vs Sem Índice

```javascript
// ============================================
// PROBLEMA: Query Sem Índice (LENTA)
// ============================================

// Query: encontrar cliente por email
db.clientes.find({ email: "joao@email.com" })

// Sem índice:
// - MongoDB examina CADA documento da collection
// - Com 10 milhões de documentos = 10 milhões de leituras
// - Cada leitura de disco = ~1ms
// - Total: ~10.000ms (10 SEGUNDOS!) ❌

// Explicação:
db.clientes.find({ email: "joao@email.com" }).explain("executionStats")
/*
{
  "executionStats": {
    "executionStages": {
      "stage": "COLLSCAN",  // ❌ BAD: Collection Scan
      "docsExamined": 10000000,  // Examinou 10 milhões
      "docsReturned": 1  // Mas só retornou 1
    },
    "executionTimeMillis": 10234
  }
}
*/

// ============================================
// SOLUÇÃO: Criar Índice
// ============================================

db.clientes.createIndex({ email: 1 })

// Query idêntica, mas muito mais rápida:
db.clientes.find({ email: "joao@email.com" })

// Com índice:
// - MongoDB usa B-tree para busca binária
// - Com 10 milhões de documentos = ~23 leituras
// - Total: ~23ms (100x mais rápido!) ✅

// Explicação:
db.clientes.find({ email: "joao@email.com" }).explain("executionStats")
/*
{
  "executionStats": {
    "executionStats": {
      "stage": "IXSCAN",  // ✅ GOOD: Index Scan
      "docsExamined": 1,  // Examinou só 1 documento
      "docsReturned": 1,  // Retornou 1
      "executionTimeMillis": 23
    }
  }
}
*/

// ============================================
// ÍNDICE COMPOSTO (CRÍTICO)
// ============================================

// Query comum: buscar transações por cliente e data
db.transacoes.find({
  cliente_id: ObjectId("..."),
  data: { $gte: new Date("2024-01-01") },
  status: "confirmado"
}).sort({ valor: -1 })

// Índice composto IDEAL (ordem importa!):
db.transacoes.createIndex({
  cliente_id: 1,      // Igualdade primeiro
  data: 1,             // Range depois
  status: 1,           // Igualdade
  valor: -1            // Sort por último
})

// Resultado: query vai de 5 segundos para 50ms ✅

// ============================================
// ÍNDICE TTL (Expiração Automática)
// ============================================

// Exemplo: logs de login que precisam ser mantidos por 30 dias
db.login_logs.insertOne({
  usuario_id: ObjectId("..."),
  ip: "192.168.1.100",
  timestamp: new Date(),
  sucesso: true
})

// Criar índice TTL
db.login_logs.createIndex(
  { timestamp: 1 },
  { expireAfterSeconds: 2592000 }  // 30 dias
)

// MongoDB remove automaticamente documents antigos
// Nenhuma query de DELETE necessária ✅

// ============================================
// ÍNDICE TEXT (Full-Text Search)
// ============================================

// Dados de produtos
db.produtos.insertMany([
  { nome: "MongoDB é um banco de dados NoSQL", descricao: "..." },
  { nome: "SQL relacional", descricao: "Banco de dados tradicional..." },
  // ...
])

// Criar índice de texto
db.produtos.createIndex({
  nome: "text",
  descricao: "text"
})

// Busca full-text
db.produtos.find({
  $text: { $search: "MongoDB NoSQL" }
})

// Com relevância (score)
db.produtos.find(
  { $text: { $search: "banco de dados" } },
  { score: { $meta: "textScore" } }
).sort({ score: { $meta: "textScore" } })

// ============================================
// ANÁLISE DE ÍNDICES
// ============================================

// Listar todos os índices
db.clientes.getIndexes()
/*
[
  { "v" : 2, "key" : { "_id" : 1 }, "name" : "_id_" },
  { "v" : 2, "key" : { "email" : 1 }, "name" : "email_1" },
  { "v" : 2, "key" : { "cpf" : 1 }, "name" : "cpf_1" }
]
*/

// Estatísticas de índice (quanto ele usa)
db.clientes.aggregate([ { $indexStats: {} } ])

// Remover índice desnecessário
db.clientes.dropIndex("nome_1")
```

---

## COMPARAÇÃO VISUAL: Estrutura SQL vs MongoDB

### Cliente com Contas e Transações

#### SQL (Normalizado)
```
CLIENTES
├─ id: 1
├─ nome: João
├─ email: joao@email.com
└─ cpf: 123.456.789-00

CONTAS
├─ id: 1
├─ cliente_id: 1
├─ numero: 12345-6
├─ saldo: 5000
└─ status: ativa

TRANSACOES
├─ id: 1
├─ conta_id: 1
├─ valor: 100
├─ data: 2024-01-15
└─ status: confirmado

QUERIES:
- Trazer cliente + contas + transações = 2-3 JOINs
- Mais complexo
- Mais lento em escala
```

#### MongoDB (Denormalizado)
```json
{
  "_id": ObjectId("..."),
  "nome": "João",
  "email": "joao@email.com",
  "cpf": "123.456.789-00",
  "contas": [
    {
      "id": ObjectId("..."),
      "numero": "12345-6",
      "saldo": 5000,
      "status": "ativa",
      "transacoes": [
        {
          "id": ObjectId("..."),
          "valor": 100,
          "data": ISODate("2024-01-15"),
          "status": "confirmado"
        }
      ]
    }
  ]
}

QUERIES:
- Trazer cliente + contas + transações = 1 query
- Simples
- Rápido
```

---

Este material pode ser usado como:
1. **Apêndice dos slides** (adicionar exemplos nos campos de texto dos slides)
2. **Material de referência** para o apresentador consultar durante Q&A
3. **Handout técnico** para participantes que querem aprofundar
4. **Base para live coding** se houver demonstração ao vivo
