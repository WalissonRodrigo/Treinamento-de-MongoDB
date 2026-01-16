# 🎓 MongoDB Enterprise Training - Audiobook Completo
## Preparação do Apresentador | Mercado Bancário do Brasil

---

## 📖 ÍNDICE DE MÓDULOS
1. **Módulo 1** - História e Motivação (20 min) - ~2500 palavras
2. **Módulo 2** - Fundamentos e Arquitetura (25 min) - ~3000 palavras
3. **Módulo 3** - Semântica e Modelo de Dados (30 min) - ~3500 palavras
4. **Módulo 4** - CRUD e Operadores (35 min) - ~4000 palavras
5. **Módulo 5** - Boas Práticas e Otimização (35 min) - ~4000 palavras
6. **Módulo 6** - Simulação de Casos Bancários e Conformidade (25 min) - ~3000 palavras
7. **Módulo 7** - Recursos e Roadmap (25 min) - ~3000 palavras
8. **Módulo 8** - Discussão Prática e Próximos Passos (25 min) - ~2500 palavras

**Tempo total: ~25.500 palavras para leitura em 4 horas**

---

# 🎬 MÓDULO 1: História e Evolução do MongoDB
**Duração: 20 minutos | Palavras: ~2500**

## Abertura

Bem-vindo a este treinamento avançado sobre MongoDB no campo Bancário do Brasil. Meu nome é Walisson Rodrigo, e vamos explorar durante as próximas 4 horas aproximadamente um dos bancos de dados mais revolucionários da história da tecnologia. Mas antes de mergulharmos em sintaxe, queries e otimizações, é fundamental entender a história de por que MongoDB existe e por que se tornou tão importante para empresas como a nossa.

## 1.1 - O Problema que MongoDB Resolveu (2007-2009)

Imagine o mundo da tecnologia em 2007. Você é um desenvolvedor trabalhando com aplicações web. Seu banco de dados é relacional—provavelmente MySQL ou Oracle. Você tem uma tabela de `usuarios`. Cada usuário tem `id`, `nome`, `email`. Simples. Funcionava bem.

Mas aí vem um requisito novo: você precisa armazenar múltiplos endereços por usuário. Ou múltiplos telefones. Em SQL, você cria uma tabela `usuarios_telefones`, uma chave estrangeira, e de repente suas queries simples se tornam JOINs complexos. Você precisa normalizar seus dados. Tudo fica mais complicado.

Esse era o problema enfrentado pelo time da **10gen** (empresa que criou MongoDB) em 2007. Eles estava(m) desenvolvendo plataformas de software como um serviço (SaaS) e percebeu que:

1. **O mismatch objeto-relacional era real**: Em programação orientada a objetos, um usuário é um objeto com propriedades aninhadas (endereços, telefones, contas bancárias). Mas em SQL, você precisa desaglomerar tudo em múltiplas tabelas.

2. **Esquemas fixos eram um pesadelo**: Quando você alterava um requisito e precisava adicionar um novo campo (tipo de endereço), você precisava fazer uma migração de banco de dados que poderia derrubar a aplicação.

3. **Escalabilidade horizontal era impossível**: SQL Relacional foi projetado para escalar verticalmente (servidores maiores). Quando você tinha MUITO dado, seus recursos eram esgotados.

A solução foi revolucionária: **E se armazenássemos dados exatamente como objetos JSON, e deixássemos o desenvolvedor estruturar os dados como bem entendesse?**

## 1.2 - MongoDB Lançado (2009): Uma Visão Radical

Em fevereiro de 2009, a 10gen lançou MongoDB publicamente. O nome vem de "humongous"—porque era projetado para lidar com quantidades gigantescas de dados.

A ideia central: **Um banco de dados orientado a documentos usando JSON/BSON**.

Naquele momento, isso era considerado radical. Quase heresia. Bancos de dados relacionais tinham 40+ anos de engenharia, otimizações, garantias ACID. MongoDB era um novato oferecendo flexibilidade em troca de... incerteza?

Mas o timing foi perfeito. A web estava explodindo. Aplicações estavam evoluindo rapidamente. O desenvolvimento ágil era o novo padrão. MongoDB oferecia o que desenvolvedores desesperadamente queriam: **esqueça o esquema, simplesmente armazene seus dados**.

**Curiosidade Técnica**: Os primeiros nomes considerados para MongoDB incluíram "DoubleDB" e "DocumentDB". A palavra "MongoDB" foi escolhida porque soa melhor em domínios (mongodb.com vs doubledb.com).

## 1.3 - Crescimento Exponencial (2010-2013)

O que aconteceu nos anos seguintes foi notável. MongoDB não apenas sobreviveu—prosperou de forma selvagem.

- **2010**: MongoDB atinge 1 milhão de downloads. Startups de tecnologia começam a usá-lo como padrão.
- **2011**: Diversas conferências MongoDB begin. Stack Overflow começa a ver perguntas em crescimento exponencial.
- **2012**: Grandes empresas começam pilotos: Foursquare, eBay, Uber, Airbnb estão todas experimentando com MongoDB.
- **2013**: MongoDB é declarado pela primeira vez como "a comunidade NoSQL de crescimento mais rápido" no mundo.

**Momento importante**: Enquanto MongoDB crescia, surgiram mitos e críticas legítimas:

- "MongoDB não tem ACID"—Verdadeiro naquela época. Cada documento era atômico, mas múltiplos documentos não eram.
- "MongoDB consome muita memória"—Parcialmente verdadeiro. Indexes duplicavam dados na memória.
- "MongoDB não é para dados críticos"—Essa crítica prejudicou sua adoção em finanças e bancos naquela época.

MongoDB respondeu aos críticos não com marketing, mas com engenharia.

## 1.4 - Virada Estratégica: Transações ACID (2016-2018)

O grande divisor de águas foi quando MongoDB finalmente implementou **transações ACID em múltiplos documentos**.

- **MongoDB 4.0 (2018)**: Transações ACID distribuídas. Essa foi a resposta definitiva ao argumento de "dados críticos não podem ir para MongoDB".

De repente, o principal argumento contra MongoDB foi eliminado. Você podia, com garantia, fazer uma transferência bancária atomicamente. Tudo ou nada. Sem exceções.

**Curiosidade Bancária**: Muitos bancos brasileiros hesitaram em adotar MongoDB por décadas porque SQL era "garantido". Mas quando as transações ACID chegaram, bancos como **Nubank e Banco Inter** começaram pilotos sérios. MongoDB não era mais um brinquedo de startup.

## 1.5 - MongoDB IPO e Era Cloud (2019-2021)

Em outubro de 2017, 10gen se renomeia para **MongoDB, Inc.** E em outubro de 2021, vão para o IPO na NASDAQ com ticker MDB.

Mas o momento mais importante nessa era foi o lançamento e maturação do **MongoDB Atlas** (2016+).

Atlas foi revolucionário porque resolveu o problema operacional do MongoDB:

- **Antes**: Você tinha que baixar MongoDB, instalar em servidores, fazer backup, monitorar, patchar, lidar com replicação.
- **Depois**: MongoDB cuida de TUDO. Você clica um botão, tem um cluster sharded em múltiplas regiões em minutos.

Atlas foi o que transformou MongoDB de um projeto técnico em um **negócio de nuvem escalável**.

**Estatística importante para contexto de negócios do setor Bancário**: MongoDB Atlas está disponível em 90+ regiões em AWS, Azure, e Google Cloud. Isso significa zero vendor lock-in—você pode rodar em multi-cloud.

## 1.6 - Era Moderna (2022-2025): IA e Vector Search

A evolução mais recente é a aposta em Inteligência Artificial.

MongoDB 5.0+ (2021+) e especialmente **MongoDB Atlas Vector Search** (2023+) representam MongoDB se reposicionando para a era de AI/ML.

- **Vector Search** permite armazenar embeddings (vetores) de documentos/imagens e fazer busca semântica.
- **Atlas AI** oferece agentes de IA que consultam seu MongoDB automaticamente.
- **MongoDB 8.0 (Outubro 2024)**: 36% mais rápido nas leituras, 59% mais rápido nas escritas.

Segundo o MongoDB 2024 Year in Review, MongoDB agora é usado por empresas como:
- **McKesson** (farmacêutica): Substituiu infraestrutura legada inteira, escalando 300x para rastrear 1.2 bilhão de contêineres.
- **NatWest** (banco britânico): 900 milhões de chamadas API/mês, processando 200 milhões de empréstimos e 100 milhões de contas a 150.000 transações/segundo.

## 1.7 - Por Que o Crescimento foi tão Acelerado?

Vamos ser honesto: SQL existia há 50 anos. Por que MongoDB venceu tão rápido?

1. **Alinhamento com Linguagens Modernas**: JavaScript (Node.js) revolucionou backend. MongoDB é JSON nativo. Duas strings JSON e você tem banco de dados + API.

2. **Simplicidade de Desenvolvimento**: Não precisa de ORM complexo. Mongoose para Node ou Mongoengine para Python era 10x simples que SQLAlchemy.

3. **Escalabilidade Horizontal Nativa**: Sharding estava no core desde o início. SQL relacional foi bolted-on.

4. **Flexibilidade de Schema**: Você pode começar com um projeto MVP, coletar dados, e DEPOIS definir schema. Em SQL, você precisa de schema perfeito de dia 1.

5. **Performance para Leitura Intensiva**: Cache de aplicação + índices MongoDB = operações muito rápidas.

## 1.8 - Crescimento Concreto em Números

Deixe-me compartilhar estatísticas reais que você pode mencionar em seu treinamento:

- **Stack Overflow**: Perguntas sobre MongoDB crescem 3x mais rápido que outras tecnologias Big Data.
- **LinkedIn Skills**: Habilidade com MongoDB em crescimento de 73% ao ano.
- **Meetup.com**: ~500% crescimento em grupos de MongoDB desde 2010.
- **Comunidade**: 60.000+ organizações globais usando MongoDB (dados de 2024).
- **Fortune 500**: Mais de 70% da Fortune 100 usa MongoDB em alguma forma.

Para o mercado Bancário do Brasil especificamente: Se você pesquisar "MongoDB financial services Brazil 2024", verá múltiplos bancos digitais e fintechs usando MongoDB em produção com bilhões de transações.

## 1.9 - A Visão de Futuro: MongoDB em 2025-2026

Para fechar este módulo, deixe-me pintar a visão de futuro:

MongoDB não está mais competindo com SQL. Essa guerra acabou. MongoDB venceu em certos cenários (NoSQL, escalável, development-friendly) e perdeu em outros (OLAP, transações complexas, relatórios).

Agora, MongoDB está competindo com **outros bancos de dados de documentos** (CouchDB), **data warehouses** (Snowflake), e **bancos vetoriais** (Pinecone).

A aposta estratégica de MongoDB é ser o **banco de dados completo para AI-native applications**:

- Dados estruturados ✓
- Vector embeddings para semantic search ✓
- Full-text search integrado ✓
- Time-series otimizado ✓
- Change streams para event-driven ✓
- Analytics com MongoDB Analytics ✓

Você não precisa mais de 5 ferramentas diferentes. MongoDB é a plataforma unificada.

## 1.10 - Resumo Executivo para Apresentação

**O que comunicar sobre história em seu treinamento**:

1. **Origem**: 2007-2009, resolvendo problema real de mismatch objeto-relacional
2. **Crescimento**: Exponencial de 2010-2013, mas com ceticismo justificado
3. **Virada**: Transações ACID em 2018 eliminaram desculpa técnica final
4. **Escalabilidade**: Atlas (2016+) resolveu problema operacional
5. **Futuro**: IA é o próximo frontier; MongoDB se reposiciona como plataforma de IA

---

# 🏗️ MÓDULO 2: Fundamentos e Arquitetura do MongoDB
**Duração: 25 minutos | Palavras: ~3000**

## Abertura

Agora que você entende POR QUE MongoDB foi criado, vamos mergulhar em COMO funciona. Neste módulo, exploraremos a arquitetura fundamental, os componentes-chave, e como MongoDB armazena e recupera dados.

## 2.1 - O Modelo Document-Oriented: O Core

Diferente de SQL que pensa em **linhas e colunas**, MongoDB pensa em **documentos**.

**Definição técnica**: Um documento MongoDB é uma estrutura de dados JSON-like que contém campos e valores. É semanticamente similar a um objeto JavaScript ou uma dicionário Python.

Exemplo de documento bancário:

```json
{
  "_id": ObjectId("507f1f77bcf86cd799439011"),
  "cliente_id": "BR123456789",
  "nome": "João da Silva",
  "cpf": "111.222.333-44",
  "email": "joao@example.com",
  "tipo": "PF",
  "saldo": 5000.50,
  "moeda": "BRL",
  "contas": [
    {
      "numero": "123456-7",
      "tipo": "corrente",
      "saldo": 3000.00,
      "ativa": true,
      "criada_em": ISODate("2020-01-15T10:00:00Z")
    },
    {
      "numero": "123456-8",
      "tipo": "poupanca",
      "saldo": 2000.50,
      "ativa": true,
      "criada_em": ISODate("2020-02-20T14:30:00Z")
    }
  ],
  "endereco": {
    "rua": "Av. Paulista",
    "numero": 1000,
    "cidade": "São Paulo",
    "estado": "SP",
    "cep": "01310-100",
    "pais": "Brasil",
    "coordenadas": {
      "tipo": "Point",
      "coordinates": [-23.5505, -46.6333]
    }
  },
  "kyc_status": "verificado",
  "data_cadastro": ISODate("2020-01-15T10:00:00Z"),
  "atualizado_em": ISODate("2024-01-10T15:45:00Z")
}
```

**Observe**: Tudo que você precisa saber sobre um cliente está em UM documento. Sem JOINs. Sem tabelas relacionadas. Sem normalização complexa.

## 2.2 - BSON: A Representação Interna

JSON é bonito para humanos, mas ineficiente para computadores.

**BSON** (Binary JSON) é o formato binário que MongoDB usa internamente para armazenar documentos em disco.

**Vantagens do BSON**:

1. **Tipos de dados ricos**: Enquanto JSON suporta apenas string, number, boolean, null, array, object—BSON adiciona:
   - Date (armazena timestamp)
   - ObjectId (identificador único)
   - Binary (dados binários puros)
   - Decimal128 (decimais de precisão arbitrária—crítico para finanças)
   - Long (inteiros 64-bit)
   - Regex (expressões regulares)
   - Code (código JavaScript)

2. **Compressão**: BSON interno é comprimido pelo storage engine WiredTiger, economizando até 80% de espaço em disco.

3. **Eficiência de Acesso**: BSON é estruturado de forma que MongoDB pode "pular" para campos específicos sem ler todo o documento.

**Curiosidade**: Decimal128 foi introduzido em MongoDB 3.4 especificamente para satisfazer requisitos de conformidade bancária. Decimais em ponto flutuante (IEEE 754) têm problemas de precisão (0.1 + 0.2 != 0.3). Bancos não podem tolerar isso. Decimal128 resolve isso.

## 2.3 - Hierarquia: Database → Collection → Document

Vamos estruturar como organizar dados no MongoDB:

```
MongoDB Instance (servidor)
  └─ banco_dados
      ├─ Collection: clientes
      │   ├─ Document 1: {_id: ..., nome: "João", ...}
      │   ├─ Document 2: {_id: ..., nome: "Maria", ...}
      │   └─ Document N: {...}
      ├─ Collection: contas
      │   ├─ Document 1: {_id: ..., cliente_id: ..., saldo: ...}
      │   └─ Document N: {...}
      ├─ Collection: transacoes
      │   └─ Document 1-M: {...}
      └─ Collection: logs
          └─ Document 1-M: {...}
```

**Database**: Namespace lógico. Na sua empresa, você pode ter `banco_producao`, `banco_desenvolvimento`, `banco_testes`.

**Collection**: Equivalente a "tabela" em SQL, mas sem esquema obrigatório. Todos os documentos em uma collection podem ter estruturas diferentes.

**Document**: O dado individual. Tem um `_id` obrigatório (chave primária), e qualquer número de campos.

## 2.4 - ObjectId: O Identificador Único

Todo documento tem um campo `_id`. É obrigatório. É a chave primária.

Se você não fornecer `_id`, MongoDB gera um **ObjectId** automaticamente.

**O que é ObjectId?**

Um ObjectId é um valor binário de 12 bytes:
- **4 bytes**: Timestamp (segundos desde epoch—quando foi criado)
- **3 bytes**: Machine identifier (qual servidor criou)
- **2 bytes**: Process id (qual processo)
- **3 bytes**: Counter (número sequencial naquele processo)

**Vantagem**: Você pode gerar ObjectIds no cliente ANTES de inserir, e estão garantidos serem únicos globalmente, sem coordenação com servidor.

**Desvantagem**: ObjectIds crescem sequencialmente, criando um padrão. Se você fizer um índice em ObjectId, o B-tree pode não ser tão eficiente quanto um UUID randômico.

**Para aplicações bancárias**, frequentemente você USA SEU PRÓPRIO ID:

```javascript
db.clientes.insertOne({
  _id: "BR123456789",  // Usar CPF como _id
  nome: "João",
  email: "joao@email.com"
})
```

Isso economiza espaço de índice e faz consultas mais rápidas.

## 2.5 - Storage Engine: WiredTiger

WiredTiger é o "coração" do MongoDB desde versão 3.0 (2015).

**Antes**: MMAPv1 era o storage engine padrão. Mapeava arquivo do banco para memória do SO (memory-mapped files). Era simples, mas tinha problemas de lock.

**Depois**: WiredTiger oferecia:

1. **Document-level locking**: Múltiplas transações podiam escrever em documentos diferentes simultaneamente. Isso aumentou throughput dramaticamente.

2. **Compression**: WiredTiger comprime documentos no disco usando snappy ou zstd compression, economizando bandwidth em replicação.

3. **Read Optimization**: Usa B-tree indexing avançado com página caching eficiente.

**Curiosidade técnica profunda**: WiredTiger foi adquirido de uma empresa chamada "WiredTiger" por MongoDB em 2014. O criador, Michael Cahill, agora é VP of Engineering no MongoDB.

Internamente, WiredTiger organiza documentos assim:

```
Index _id (B-tree)
  └─ Leaf page: _id → recordId (pointer)
      └─ Hidden index: recordId → BSON comprimido
```

Essa indireção (index → recordId → documento) é similar a PostgreSQL e permite que MongoDB atualize documentos sem reorganizar toda a página.

## 2.6 - Replica Sets: Alta Disponibilidade

Um Replica Set é um grupo de servidores MongoDB que replicam dados entre si.

**Composição típica**:

- **1 Primary**: Recebe TODAS as escritas. Replication source.
- **2+ Secondaries**: Copiam dados da primary, podem servir LEITURAS.
- **Arbiter** (opcional): Participa de eleição de novo primary se primary cai, mas NÃO armazena dados.

**Exemplo para Bancos Brasileiros**:

```
São Paulo (Primary)
  ↓ replica (oplog)
Rio de Janeiro (Secondary)
  ↓ replica (oplog)
Brasília (Secondary)
  ↓ ack
Belo Horizonte (Arbiter - apenas eleição)
```

**Como funciona**:

1. Cliente conecta no Replica Set via `mongodb://rs.example.com/?replicaSet=myRS`
2. Driver descobre qual é Primary consultando um server qualquer
3. Escritas vão SEMPRE para Primary
4. Leituras podem ir para Primary ou Secondary (configurável)

**Write Concern**: Você especifica "quantas cópias confirmam antes de eu considerar a escrita completa"

- `{w: 1}` = Apenas Primary confirmou (rápido, menos seguro)
- `{w: 2}` = Primary + 1 Secondary confirmaram (equilibrado)
- `{w: 3}` = Primary + 2 Secondaries confirmaram (lento, muito seguro)

**Read Preference**: Você especifica "de onde ler"

- `primary` = Sempre ler da Primary (consistência forte)
- `primaryPreferred` = Primary, mas Secondary se Primary indisponível (padrão)
- `secondary` = Só Secondary (escalabilidade de leitura, eventual consistency)

**Failover automático**: Se Primary cai, Secondaries votam para promover uma Secondary para nova Primary. Isso leva 10-30 segundos típicamente.

## 2.7 - Sharding: Escalabilidade Horizontal

Replica Sets resolvem **disponibilidade**. Sharding resolve **escalabilidade de dados e throughput**.

**Problema**: Você tem 10 bilhões de documentos de clientes. Um servidor não aguenta 100GB de RAM.

**Solução**: Particione (shard) os dados entre múltiplos servidores.

```
Dados: 10 bilhões de clientes
      ├─ Shard 1: 1-2.5 bilhões (cpf < "333...")
      ├─ Shard 2: 2.5-5 bilhões (cpf entre "333..." e "666...")
      ├─ Shard 3: 5-7.5 bilhões (cpf entre "666..." e "999...")
      └─ Shard 4: 7.5-10 bilhões (cpf >= "999...")
```

**Componentes de Sharding**:

1. **Shard**: Um Replica Set com um subconjunto dos dados
2. **Mongos**: Router que direciona queries para o shard correto
3. **Config Servers**: Armazenam metadados (qual range vai para qual shard)

**Shard Key**: O campo que determina para qual shard um documento vai.

```javascript
// Escolher shard key
sh.shardCollection("banco.clientes", {cpf: 1})

// Agora:
db.clientes.insertOne({cpf: "111.222.333-44", ...})  // → Shard 1
db.clientes.insertOne({cpf: "444.555.666-77", ...})  // → Shard 2
db.clientes.insertOne({cpf: "777.888.999-00", ...})  // → Shard 3
```

**Curiosidade de Sharding**: Escolher shard key ERRADO é uma dos maiores erros em MongoDB produção.

Exemplo RUIM de shard key:
- `status`: Apenas 3 valores (ativo/inativo/suspenso) → Desbalanceamento extremo
- `tipo_documento`: Apenas 2 valores (PF/PJ) → Mesma coisa
- `mes`: Apenas 12 valores → Mesmo problema

Exemplo BOM de shard key:
- `cpf`: Millions de valores, distribuição uniforme ✓
- `email`: Millions de valores, uniforme ✓
- UUID aleatório: Perfeitamente distribuído ✓

## 2.8 - Índices: Aceleração Fundamental

Sem índices, MongoDB precisa varrer TODA a collection para encontrar um documento.

Com índices, MongoDB usa B-tree para encontrar em O(log n).

**Tipos de índices**:

1. **Single-field index**: Um campo
   ```javascript
   db.clientes.createIndex({email: 1})
   ```

2. **Compound index**: Múltiplos campos (crucial!)
   ```javascript
   db.transacoes.createIndex({cliente_id: 1, data: -1, status: 1})
   // Otimiza queries como:
   // - find({cliente_id: X})
   // - find({cliente_id: X, data: {$gte: Y}})
   // - find({cliente_id: X, data: {$gte: Y}, status: Z})
   ```

3. **TTL index**: Remove documentos automaticamente após tempo
   ```javascript
   db.sessions.createIndex({criado_em: 1}, {expireAfterSeconds: 3600})
   // Sessões expiram automaticamente em 1 hora
   ```

4. **Text index**: Full-text search
5. **Geospatial index**: Buscas de localização (lat/long)
6. **Sparse index**: Apenas documentos que têm o campo
7. **Unique index**: Não permite duplicatas

## 2.9 - Transações ACID (Modern MongoDB)

MongoDB 4.0+ (2018+) oferece **transações ACID em múltiplos documentos**.

```javascript
const session = client.startSession();
try {
  session.startTransaction();
  
  // Débito na conta origem
  db.contas.updateOne(
    {_id: contaOrigem},
    {$inc: {saldo: -1000}},
    {session}
  );
  
  // Crédito na conta destino
  db.contas.updateOne(
    {_id: contaDestino},
    {$inc: {saldo: +1000}},
    {session}
  );
  
  // TUDO ou NADA
  await session.commitTransaction();
} catch (err) {
  await session.abortTransaction();
  throw err;
} finally {
  await session.endSession();
}
```

**Garantias ACID**:

- **Atomicidade**: Tudo faz commit ou tudo faz rollback
- **Consistência**: Saldo nunca fica inválido
- **Isolamento**: Outras transações não veem estado intermediário (snapshot isolation)
- **Durabilidade**: Uma vez commitado, persiste mesmo se servidor cair

**Limitações importantes**:

- Transações entre shards são suportadas, mas mais lentas
- Transações devem completar em 60 segundos (padrão)
- Não podem fazer DDL (criar índice) dentro de transação

## 2.10 - Atlas vs Self-Managed

**Self-Managed**: Você baixa MongoDB, instala em servidores, gerencia tudo

- Backup manual ✗
- Monitoramento ✗
- Patching ✗
- Replicação ✗
- Sharding ✗

**MongoDB Atlas**: Versão cloud gerenciada

- Backup automático ✓
- Monitoramento built-in ✓
- Patching automático ✓
- Replicação automática ✓
- Sharding com 1 clique ✓
- Multi-cloud (AWS, Azure, GCP) ✓
- PITR (Point-in-Time Recovery) ✓

Para o mercado Bancário do Brasil, Atlas é provavelmente o caminho ideal—eliminam toda overhead operacional.

## 2.11 - Resumo Arquitetura

```
Aplicação
   ↓
Drivers MongoDB (node, python, java, etc)
   ↓
[Mongos Router - se sharded]
   ↓
Primary + Secondaries (Replica Set)
   ↓
WiredTiger Storage Engine
   ↓
Índices B-tree
   ↓
Disco (BSON comprimido)
```

---

# 📊 MÓDULO 3: Semântica, Modelo de Dados e Design
**Duração: 30 minutos | Palavras: ~3500**

## Abertura

Agora que você entende a arquitetura, vamos abordar a decisão MAIS importante em MongoDB: **Como estruturar seus dados?**

Esse módulo é crítico porque decisões de design tomadas hoje vai(m) assombrar você por anos. A boa notícia: MongoDB é flexível. A má notícia: flexibilidade demais leva a decisões ruins.

## 3.1 - O Paradoxo do Schemaless

MongoDB é "schemaless"—significa que NÃO precisa de schema predefinido.

Você pode inserir documentos completamente diferentes na mesma collection:

```javascript
db.clientes.insertOne({nome: "João", cpf: "111.222.333-44"})
db.clientes.insertOne({razao_social: "ACME Corp", cnpj: "12.345.678/0001-99"})
db.clientes.insertOne({apelido: "Ze Maria"})  // Falta muito! Mas OK!
```

Isso é **liberador**—você pode começar a guardar dados sem estar 100% certo da estrutura.

Mas há um preço: seu código precisa ser defensivo.

```javascript
// Preciso checar se campo existe
const cpf = cliente.cpf || cliente.cnpj || null;
if (!cpf) {
  throw new Error("Cliente sem identificador!");
}
```

**Solução moderna**: MongoDB 3.6+ oferece **Schema Validation**.

```javascript
db.createCollection("clientes", {
  validator: {
    $jsonSchema: {
      bsonType: "object",
      required: ["_id", "tipo"],
      properties: {
        _id: {bsonType: "string"},
        tipo: {enum: ["PF", "PJ"]},
        nome: {bsonType: "string"},
        cpf: {bsonType: "string"},
        cnpj: {bsonType: "string"},
        email: {bsonType: "string", pattern: "^.*@.*$"}
      }
    }
  }
})
```

Agora MongoDB **valida na escrita**. Não é schema puro, mas oferece guardrails.

## 3.2 - Embedding vs Referencing: A Decisão Crítica

Essa é a decisão mais importante em design MongoDB.

**Scenario**: Um cliente tem múltiplas contas bancárias.

### Opção 1: Embedding (Denormalização)

```javascript
{
  _id: "CPF123",
  nome: "João",
  email: "joao@email.com",
  contas: [  // ← Embedded array
    {
      numero: "123456-7",
      tipo: "corrente",
      saldo: 3000.00
    },
    {
      numero: "123456-8",
      tipo: "poupanca",
      saldo: 2000.50
    }
  ]
}
```

**Vantagens**:
- Fetch um cliente = pegam TUDO que precisa (contas incluídas)
- Atômico: atualize o cliente uma vez, contas estão incluídas
- Performance: 1 query em vez de 2

**Desvantagens**:
- Se contas crescem muito, documento fica grande (16MB limite)
- Atualizar uma conta específica requer atualizar documento inteiro
- Difícil fazer queries complexas em contas sem sair do cliente

### Opção 2: Referencing (Normalização)

```javascript
// Documento de Cliente
{
  _id: "CPF123",
  nome: "João",
  email: "joao@email.com"
  // contas referenciadas, não embutidas
}

// Documentos de Conta
{
  _id: ObjectId(...),
  cliente_id: "CPF123",  // ← Referência
  numero: "123456-7",
  tipo: "corrente",
  saldo: 3000.00
}
```

**Vantagens**:
- Documentos menores
- Cada conta pode ser atualizada independentemente
- Contas podem existir sem cliente (histórico)
- Queries complexas em contas são fáceis

**Desvantagens**:
- Fetch um cliente requer 2+ queries (cliente + contas)
- Precisa fazer JOIN (MongoDB chamado `$lookup`)
- Menos atômico: atualize cliente e conta em 2 operações

### Recomendação Pragmática

**Use embedding quando**:
- Relação é 1:1 ou 1:poucos (1-10 documentos filhos)
- Dados do filho são acessados 95%+ das vezes junto com pai
- Filho não é atualizado independentemente
- Filho não é muito maior que pai

**Use referencing quando**:
- Relação é 1:muitos (100+ filhos)
- Filhos são acessados frequentemente sem pai
- Filhos são atualizados independentemente
- Dados são compartilhados (ex: um endereço para múltiplos clientes)

**Para aplicação bancária**:

```javascript
// EMBEDDING para endereço (1:1)
{
  _id: "CPF123",
  nome: "João",
  endereco: {
    rua: "Av. Paulista 1000",
    cidade: "São Paulo",
    estado: "SP"
  }
}

// REFERENCING para transações (1:muito)
db.clientes.findOne({_id: "CPF123"})
db.transacoes.find({cliente_id: "CPF123"}).sort({data: -1}).limit(100)
```

## 3.3 - Tipos de Dados: A Importância de Escolher Certo

MongoDB suporta vários tipos BSON, e escolher errado causa problemas.

### String vs ObjectId vs IDs Customizados

```javascript
// OPÇÃO 1: ObjectId (padrão, gera automaticamente)
{
  _id: ObjectId("507f1f77bcf86cd799439011"),
  ...
}

// OPÇÃO 2: String com UUID
{
  _id: "a1b2c3d4-e5f6-4708-9a10-b11c12d13e14",
  ...
}

// OPÇÃO 3: String com significado (ex: CPF)
{
  _id: "111.222.333-44",
  nome: "João"
}

// OPÇÃO 4: Integer
{
  _id: 12345,
  ...
}
```

**Para os Bancos**: Usando CPF como `_id` é pragmático porque:
- CPF é único e imutável
- Economiza espaço no índice
- Queries por CPF são rápidas (hit na primary key)
- Semanticamente significativo para auditoria

### Decimal vs Float vs Integer

**NUNCA** use float (double) para dinheiro!

```javascript
// ❌ ERRADO
{
  saldo: 100.00  // Pode ser 99.99999999999999 ou 100.00000000000001
}

// ✓ CORRETO
{
  saldo: Decimal128("100.00")  // Precisão exata
}
```

`Decimal128` foi adicionado ao MongoDB 3.4 especificamente para casos de uso financeiro.

### Date vs String vs Timestamp

```javascript
// ❌ ERRADO
{
  data_transacao: "2024-01-15"  // String é ineficiente e hard to query
}

// ✓ CORRETO
{
  data_transacao: ISODate("2024-01-15T10:30:00Z")  // Tipo Date
}
```

Com tipo Date, você pode fazer:
```javascript
db.transacoes.find({
  data_transacao: {$gte: ISODate("2024-01-01"), $lte: ISODate("2024-12-31")}
})
```

## 3.4 - Padrões de Design Avançados

### Padrão 1: Outlier Pattern

**Problema**: Array que cresce indefinidamente causa problema.

```javascript
// ❌ Problema: Array cresce para milhões de elementos
{
  _id: "CPF123",
  nome: "João",
  transacoes: [  // 5 milhões de elementos!
    {data: "...", valor: 100},
    {data: "...", valor: 200},
    // ... 5 milhões mais
  ]
}
```

**Solução**: Separate outliers

```javascript
// ✓ Solução
{
  _id: "CPF123",
  nome: "João",
  ultimas_transacoes: [  // Apenas últimas 100
    {data: "...", valor: 100},
    {data: "...", valor: 200},
  ]
}

// Transações antigas em collection separada
db.transacoes_historico.find({cliente_id: "CPF123"})
```

### Padrão 2: Subset Pattern

**Problema**: Documento de cliente tem 1MB, mas queries frequentes só precisam de 10KB.

```javascript
// ❌ Problema
{
  _id: "CPF123",
  nome: "João",
  email: "joao@email.com",
  endereco: {...},  // 50KB
  telefones: [...],  // 20KB
  historico_completo: [...]  // 800KB
}
```

**Solução**: Denormalize subset frequente

```javascript
// ✓ Solução
{
  _id: "CPF123",
  nome: "João",
  email: "joao@email.com",
  // Resumo rápido
  saldo_total: 5000.00,
  numero_contas: 2,
  status: "ativo"
}

// Dados completos em collection separada ou não-indexed
db.clientes_completo.findOne({_id: "CPF123"})
```

### Padrão 3: Computed Pattern

**Problema**: Calcular saldo total requer sumar todas as contas. Lento em queries.

**Solução**: Precalcule e armazene

```javascript
{
  _id: "CPF123",
  nome: "João",
  contas: [
    {numero: "123456-7", saldo: 3000},
    {numero: "123456-8", saldo: 2000}
  ],
  saldo_total: 5000,  // ← Cached/computed
  atualizado_em: ISODate("2024-01-15T10:00:00Z")
}
```

Quando saldo de conta muda, atualize também o total:

```javascript
db.clientes.updateOne(
  {_id: "CPF123"},
  {
    $inc: {"contas.0.saldo": -100, "saldo_total": -100},
    $set: {"atualizado_em": new Date()}
  }
)
```

### Padrão 4: Bucket Pattern (Time-series)

**Problema**: 1 documento por métrica por segundo = explosão de documentos.

```javascript
// ❌ Problema: 86.400 documentos POR DIA POR MÉTRICA
{timestamp: ISODate("2024-01-15T00:00:00Z"), saldo: 5000}
{timestamp: ISODate("2024-01-15T00:00:01Z"), saldo: 4999}
{timestamp: ISODate("2024-01-15T00:00:02Z"), saldo: 5001}
// ...
```

**Solução**: Agrupar em buckets (1 documento por hora)

```javascript
// ✓ Solução
{
  _id: ObjectId(...),
  data: ISODate("2024-01-15T00:00:00Z"),  // Hora
  cliente_id: "CPF123",
  metricas: [
    {timestamp: ISODate("2024-01-15T00:00:00Z"), saldo: 5000},
    {timestamp: ISODate("2024-01-15T00:00:01Z"), saldo: 4999},
    {timestamp: ISODate("2024-01-15T00:00:02Z"), saldo: 5001},
    // ... até 3600 registros (1 hora)
  ]
}
```

Agora você tem 86.400 documentos POR MÊS (não por dia).

## 3.5 - Validação de Schema

Como mencionado antes, use schema validation para enforçar consistência:

```javascript
db.createCollection("transacoes", {
  validator: {
    $jsonSchema: {
      bsonType: "object",
      required: ["_id", "cliente_id", "valor", "data", "status"],
      properties: {
        _id: {bsonType: "objectId"},
        cliente_id: {bsonType: "string"},
        valor: {bsonType: "decimal"},
        data: {bsonType: "date"},
        status: {enum: ["pendente", "processada", "rejeitada"]},
        tipo: {enum: ["débito", "crédito"]},
        descricao: {bsonType: "string"}
      }
    }
  }
})
```

Agora, se alguém tentar inserir transação sem `valor`:

```javascript
db.transacoes.insertOne({
  cliente_id: "CPF123",
  data: new Date()
  // falta 'valor'
})
// → Error: Document failed validation
```

## 3.6 - Migration Strategy

Nem sempre você consegue "redesenhar" sua collection do zero.

**Como migrar dados com zero downtime**:

```javascript
// 1. Criar nova collection com novo schema
db.createCollection("clientes_v2", {validator: {...}})

// 2. Copiar dados antigos
db.clientes.find().forEach(doc => {
  db.clientes_v2.insertOne(doc)  // Pode transformar aqui
})

// 3. Criar índices
db.clientes_v2.createIndex({cpf: 1})

// 4. Atualizar aplicação para usar clientes_v2
// (dual-write pattern é recomendado)

// 5. Validar dados
assert.eq(db.clientes.count(), db.clientes_v2.count())

// 6. Drop collection antiga
db.clientes.drop()

// 7. Renomear
db.clientes_v2.renameCollection("clientes")
```

Alternativamente, MongoDB oferece **Online Collection Validation** em versões recentes para menos downtime.

## 3.7 - Exemplo Completo: Design de Sistema Bancário

Vamos projetar um banco simples no MongoDB:

```javascript
// Clientes (1 documento por cliente)
{
  _id: "CPF123",
  nome: "João Silva",
  email: "joao@email.com",
  tipo: "PF",
  data_cadastro: ISODate("2020-01-15"),
  status: "ativo",
  kyc_status: "verificado",
  saldo_total: Decimal128("5000.00"),  // cached
  numero_contas: 2
}

// Contas (1 documento por conta)
{
  _id: ObjectId(...),
  numero: "123456-7",
  cliente_id: "CPF123",
  tipo: "corrente",
  saldo: Decimal128("3000.00"),
  criada_em: ISODate("2020-01-15"),
  ativa: true
}

// Transações (1 documento por transação)
{
  _id: ObjectId(...),
  cliente_id: "CPF123",
  conta_origem: "123456-7",
  conta_destino: "654321-9",
  valor: Decimal128("500.00"),
  data: ISODate("2024-01-15T10:30:00Z"),
  status: "processada",
  tipo: "transferencia",
  descricao: "Transferência para amigo"
}

// Índices críticos
db.clientes.createIndex({cpf: 1}, {unique: true})
db.contas.createIndex({cliente_id: 1, ativa: 1})
db.transacoes.createIndex({cliente_id: 1, data: -1})
db.transacoes.createIndex({conta_origem: 1, data: -1})
db.transacoes.createIndex({conta_destino: 1, data: -1})

// Schema validation
db.createCollection("transacoes", {
  validator: {
    $jsonSchema: {
      bsonType: "object",
      required: ["cliente_id", "valor", "data", "status"],
      properties: {
        valor: {bsonType: "decimal"},
        status: {enum: ["pendente", "processada", "rejeitada"]}
        // ...
      }
    }
  }
})
```

## 3.8 - Resumo Decisões de Design

1. **Embedding vs Referencing**: Depende da relação (1:1 embed, 1:muitos reference)
2. **Tipos de Dados**: Use Decimal128 para dinheiro, Date para timestamps
3. **Padrões Avançados**: Outlier, Subset, Computed, Bucket resolvem problemas comuns
4. **Schema Validation**: Use para enforçar consistência
5. **Índices**: Planeje índices ANTES de dados em produção
6. **Versioning**: Tenha estratégia para evolução de schema

---

# 🔍 MÓDULO 4: CRUD, Operadores e Queries
**Duração: 35 minutos | Palavras: ~4000**

[Continuação expandida com exemplos bancários práticos de CRUD, operadores de comparação, lógicos, aggregation pipeline com casos reais...]

## Abertura

Agora que você entende o modelo de dados, vamos aos comandos reais. Este módulo é prático—aprenderemos a INSERT, READ, UPDATE, DELETE dados, e exploraremos operadores poderosos para queries complexas.

## 4.1 - CREATE: Inserindo Documentos

### Insert One

```javascript
db.clientes.insertOne({
  _id: "CPF123",
  nome: "João Silva",
  email: "joao@email.com",
  saldo: Decimal128("5000.00"),
  data_cadastro: new Date()
})
```

Retorna:
```javascript
{
  "acknowledged": true,
  "insertedId": "CPF123"
}
```

### Insert Many

```javascript
db.clientes.insertMany([
  {_id: "CPF124", nome: "Maria", email: "maria@email.com"},
  {_id: "CPF125", nome: "Pedro", email: "pedro@email.com"}
], {ordered: true})  // ordered: false para continuar se erro
```

**Características importantes**:

- `_id` é obrigatório (gerado se não fornecido)
- `insertMany` é MUITO mais rápido que múltiplos `insertOne` (batch)
- `ordered: false` permite inserir mesmo se um documento falhar

### Write Concern

Você pode controlar quantas réplicas confirmam antes de "OK":

```javascript
db.clientes.insertOne(
  {_id: "CPF126", nome: "Lucas"},
  {writeConcern: {w: 3}}  // Aguarde 3 réplicas confirmarem
)
```

- `w: 1` = Apenas primary (rápido)
- `w: 2` = Primary + 1 secondary (equilibrado)
- `w: "majority"` = Maioria de réplicas (seguro)

## 4.2 - READ: Consultando Documentos

### Find Básico

```javascript
// Encontrar TUDO
db.clientes.find({})

// Encontrar com filtro
db.clientes.find({nome: "João"})

// Múltiplos critérios (AND implícito)
db.clientes.find({nome: "João", email: "joao@email.com"})
```

### Projeção (Select Fields)

```javascript
// Retornar apenas campos específicos
db.clientes.find(
  {nome: "João"},
  {_id: 0, nome: 1, email: 1}  // 0=excluir, 1=incluir
)

// Resultado
{nome: "João", email: "joao@email.com"}
```

### Sort e Limit

```javascript
// Ordenar (1=crescente, -1=decrescente)
db.clientes.find({})
  .sort({saldo: -1})  // Maior saldo primeiro
  .limit(10)          // Apenas top 10

// Paginação
db.clientes.find({})
  .sort({_id: 1})
  .skip(20)           // Skip first 20
  .limit(10)          // Depois take 10
```

### Find One

```javascript
// Retorna PRIMEIRO documento que match
db.clientes.findOne({email: "joao@email.com"})

// Null se não encontrar
```

### Count

```javascript
// Contar documentos
db.clientes.countDocuments({status: "ativo"})

// Retorna: 15
```

## 4.3 - Operadores de Comparação

### $eq (Igual)

```javascript
db.transacoes.find({status: {$eq: "processada"}})
// Equivalente a:
db.transacoes.find({status: "processada"})
```

### $ne (Não igual)

```javascript
// Transações que NÃO foram rejeitadas
db.transacoes.find({status: {$ne: "rejeitada"}})
```

### $gt, $gte, $lt, $lte

```javascript
// Transações maiores que 1000
db.transacoes.find({valor: {$gt: Decimal128("1000")}})

// Transações entre 500 e 2000
db.transacoes.find({
  valor: {
    $gte: Decimal128("500"),
    $lte: Decimal128("2000")
  }
})

// Transações nos últimos 30 dias
db.transacoes.find({
  data: {
    $gte: ISODate(new Date(new Date().getTime() - 30*24*60*60*1000))
  }
})
```

### $in e $nin

```javascript
// Transações com status pendente OU processada
db.transacoes.find({status: {$in: ["pendente", "processada"]}})

// Clientes que NÃO têm tipo PF nem PJ (erro de dados!)
db.clientes.find({tipo: {$nin: ["PF", "PJ"]}})
```

### $exists

```javascript
// Clientes que têm CPF registrado
db.clientes.find({cpf: {$exists: true}})

// Clientes que NÃO têm telefone
db.clientes.find({telefone: {$exists: false}})
```

### $type

```javascript
// Documentos onde saldo é tipo decimal
db.clientes.find({saldo: {$type: "decimal"}})

// Documentos onde email é string
db.clientes.find({email: {$type: "string"}})
```

### $regex

```javascript
// Clientes com email da Hotmail
db.clientes.find({email: {$regex: "hotmail\\.com$"}})

// Case-insensitive
db.clientes.find({
  nome: {$regex: "joão", $options: "i"}
})
```

## 4.4 - Operadores Lógicos

### AND (Implícito)

```javascript
// Encontrar clientes premium que estão ativos
db.clientes.find({tipo: "PJ", status: "ativo"})
// Automaticamente AND
```

### OR

```javascript
// Transações que foram rejeitadas OU pendentes
db.transacoes.find({
  $or: [
    {status: "rejeitada"},
    {status: "pendente"}
  ]
})
```

### NOT

```javascript
// Clientes que NÃO têm status "suspenso"
db.clientes.find({status: {$not: {$eq: "suspenso"}}})

// Equivalente (mais simples):
db.clientes.find({status: {$ne: "suspenso"}})
```

### NOR

```javascript
// Clientes que não são ativas E não têm KYC verificado
db.clientes.find({
  $nor: [
    {ativa: false},
    {kyc_status: {$ne: "verificado"}}
  ]
})
```

## 4.5 - Operadores de Array

### $elemMatch

```javascript
// Clientes com pelo menos UMA conta ativa
db.clientes.find({
  contas: {
    $elemMatch: {ativa: true, saldo: {$gt: Decimal128("0")}}
  }
})
```

### $all

```javascript
// Documentos que têm TODOS os status especificados
db.eventos.find({tags: {$all: ["importante", "urgente"]}})
```

### Array Index

```javascript
// Primeira conta de cada cliente
db.clientes.find({}, {"contas.0": 1})

// Contas a partir do índice 1
db.clientes.find({"contas.1": {$exists: true}})
```

## 4.6 - UPDATE: Modificando Documentos

### $set (Definir valor)

```javascript
// Atualizar email de um cliente
db.clientes.updateOne(
  {_id: "CPF123"},
  {$set: {email: "novo@email.com"}}
)

// Atualizar múltiplos campos
db.clientes.updateOne(
  {_id: "CPF123"},
  {
    $set: {
      email: "novo@email.com",
      atualizado_em: new Date()
    }
  }
)
```

### $inc (Incrementar)

```javascript
// Adicionar 100 ao saldo
db.clientes.updateOne(
  {_id: "CPF123"},
  {$inc: {saldo: Decimal128("100")}}
)

// Decrementar
db.clientes.updateOne(
  {_id: "CPF123"},
  {$inc: {saldo: Decimal128("-50")}}
)
```

### $unset (Remover campo)

```javascript
// Remover campo de telefone antigo
db.clientes.updateOne(
  {_id: "CPF123"},
  {$unset: {telefone_antigo: ""}}  // valor irrelevante
)
```

### $push (Adicionar a array)

```javascript
// Adicionar uma transação ao histórico
db.clientes.updateOne(
  {_id: "CPF123"},
  {
    $push: {
      transacoes: {
        data: new Date(),
        valor: Decimal128("500"),
        tipo: "crédito"
      }
    }
  }
)
```

### $pull (Remover de array)

```javascript
// Remover todas as contas inativas
db.clientes.updateOne(
  {_id: "CPF123"},
  {
    $pull: {contas: {ativa: false}}
  }
)
```

### $addToSet (Adicionar se único)

```javascript
// Adicionar email à lista de emails (sem duplicar)
db.clientes.updateOne(
  {_id: "CPF123"},
  {
    $addToSet: {emails: "novo@email.com"}
  }
)
```

### Update Many

```javascript
// Atualizar VÁRIOS clientes
db.clientes.updateMany(
  {status: "inativo", data_cadastro: {$lt: ISODate("2020-01-01")}},
  {$set: {status: "excluido"}}
)

// Resultado
{
  "acknowledged": true,
  "modifiedCount": 1523
}
```

### Upsert

```javascript
// Atualizar se existe, inserir se não
db.clientes.updateOne(
  {_id: "CPF999"},
  {
    $set: {
      nome: "Cliente Novo",
      email: "novo@email.com",
      data_cadastro: new Date()
    }
  },
  {upsert: true}
)
```

Se CPF999 não existe, será inserido. Se existe, será atualizado.

## 4.7 - DELETE: Removendo Documentos

### Delete One

```javascript
// Remover UM documento
db.transacoes.deleteOne({_id: ObjectId("...")})
```

### Delete Many

```javascript
// Remover MÚLTIPLOS documentos
db.transacoes.deleteMany({status: "rejeitada", data: {$lt: ISODate("2023-01-01")}})

// Resultado
{
  "acknowledged": true,
  "deletedCount": 450
}
```

### CUIDADO: Delete All

```javascript
// ⚠️ PERIGO: Deleta TUDO!
db.clientes.deleteMany({})

// Sempre use em ambiente de testes apenas
```

## 4.8 - Aggregation Pipeline: Processamento Avançado

Aggregation é como SQL `GROUP BY` + `ORDER BY` + `JOIN` combinados.

```javascript
db.transacoes.aggregate([
  {$match: {status: "processada"}},      // WHERE
  {$group: {_id: "$cliente_id", total: {$sum: "$valor"}}},  // GROUP BY
  {$sort: {total: -1}},                  // ORDER BY
  {$limit: 10}                           // LIMIT
])
```

### $match (Filtragem)

```javascript
// Transações dos últimos 30 dias
db.transacoes.aggregate([
  {
    $match: {
      data: {$gte: ISODate("2023-12-15")},
      status: "processada"
    }
  }
])
```

### $group (Agregação)

```javascript
// Total por cliente
db.transacoes.aggregate([
  {
    $group: {
      _id: "$cliente_id",
      total: {$sum: "$valor"},
      quantidade: {$sum: 1},
      media: {$avg: "$valor"},
      maximo: {$max: "$valor"},
      minimo: {$min: "$valor"}
    }
  }
])

// Resultado
{
  _id: "CPF123",
  total: Decimal128("10000"),
  quantidade: 50,
  media: Decimal128("200"),
  maximo: Decimal128("5000"),
  minimo: Decimal128("10")
}
```

### $sort (Ordenação)

```javascript
// Clientes com maior volume de transações primeiro
db.transacoes.aggregate([
  {$group: {_id: "$cliente_id", total: {$sum: "$valor"}}},
  {$sort: {total: -1}},
  {$limit: 10}
])
```

### $project (Transformação)

```javascript
// Retornar campos específicos e criar novos
db.transacoes.aggregate([
  {
    $project: {
      cliente: "$cliente_id",
      valor: "$valor",
      valor_em_dolares: {$multiply: ["$valor", 5.0]},  // Convert
      ano: {$year: "$data"},
      mes: {$month: "$data"},
      _id: 0  // Excluir _id
    }
  }
])
```

### $lookup (JOIN)

```javascript
// JOINar transações com clientes
db.transacoes.aggregate([
  {
    $lookup: {
      from: "clientes",
      localField: "cliente_id",
      foreignField: "_id",
      as: "cliente_info"
    }
  },
  {$unwind: "$cliente_info"},  // Desaglomerar array
  {
    $project: {
      cliente_nome: "$cliente_info.nome",
      cliente_email: "$cliente_info.email",
      valor: "$valor",
      data: "$data"
    }
  }
])

// Resultado
{
  cliente_nome: "João Silva",
  cliente_email: "joao@email.com",
  valor: Decimal128("500"),
  data: ISODate("2024-01-15T10:00:00Z")
}
```

### $facet (Múltiplas Agregações)

```javascript
// Calcular múltiplas estatísticas em uma query
db.transacoes.aggregate([
  {
    $facet: {
      por_status: [
        {$group: {_id: "$status", count: {$sum: 1}}}
      ],
      por_tipo: [
        {$group: {_id: "$tipo", count: {$sum: 1}}}
      ],
      estatisticas: [
        {
          $group: {
            _id: null,
            total: {$sum: "$valor"},
            media: {$avg: "$valor"},
            maximo: {$max: "$valor"}
          }
        }
      ]
    }
  }
])

// Resultado
{
  por_status: [{_id: "processada", count: 1000}, ...],
  por_tipo: [{_id: "débito", count: 500}, ...],
  estatisticas: [{total: ..., media: ..., maximo: ...}]
}
```

## 4.9 - Explain: Entendendo Execução

```javascript
// Ver como a query é executada
db.clientes.find({cpf: "111.222.333-44"}).explain("executionStats")

// Resultado mostra:
{
  "executionStages": {
    "stage": "COLLSCAN",  // ← RUIM: Full collection scan
    "nReturned": 1,
    "executionTimeMillis": 150
  }
}

// Se houver índice em CPF:
{
  "executionStages": {
    "stage": "IXSCAN",  // ← BOM: Index scan
    "nReturned": 1,
    "executionTimeMillis": 1  // 150x mais rápido!
  }
}
```

## 4.10 - Bulk Operations

Para operações em larga escala, use bulk:

```javascript
const bulk = db.clientes.initializeUnorderedBulkOp();

for (let i = 0; i < 10000; i++) {
  bulk.insert({_id: `CPF${i}`, nome: `Cliente ${i}`});
}

bulk.execute();
```

Muito mais rápido que `insertMany`.

---

# 💾 MÓDULO 5: Boas Práticas e Otimização
**Duração: 35 minutos | Palavras: ~4000**

[Inclui: Indexing strategy, Performance tuning, Connection pooling, Caching patterns, Batching, Data modeling decisions for scale, Monitoring, Security best practices...]

## Abertura

Agora você sabe como usar MongoDB. Mas "saber usar" e "usar bem" são coisas diferentes. Este módulo é sobre os 20% de conhecimento que gera 80% do valor em produção.

## 5.1 - Estratégia de Índices: A Prioridade #1

### Índice Composto: A Chave

```javascript
// ❌ ERRADO: Múltiplos índices simples
db.transacoes.createIndex({cliente_id: 1})
db.transacoes.createIndex({data: 1})
db.transacoes.createIndex({status: 1})

// MongoDB precisa escolher 1 índice. Se escolhe errado, fica lento.

// ✓ CORRETO: 1 índice composto
db.transacoes.createIndex({
  cliente_id: 1,
  data: -1,
  status: 1
})

// Agora otimiza:
db.transacoes.find({cliente_id: X})  // Hit índice
db.transacoes.find({cliente_id: X, data: {$gte: Y}})  // Hit índice
db.transacoes.find({cliente_id: X, data: {$gte: Y}, status: Z})  // Hit índice
```

### ESR Rule (Equality-Sort-Range)

Ao criar índices compostos, a ordem importa:

```javascript
// ❌ ERRADO
db.transacoes.createIndex({data: -1, status: 1, cliente_id: 1})

// ✓ CORRETO (ESR)
db.transacoes.createIndex({
  status: 1,        // E (Equality) - operador $eq
  data: -1,         // S (Sort) - usado em sort()
  cliente_id: 1     // R (Range) - operador $gte, $lt, etc
})
```

### Análise de Índices

```javascript
// Ver todos os índices
db.transacoes.getIndexes()

// Resultado
[
  {key: {_id: 1}},  // Sempre existe
  {key: {cliente_id: 1, data: -1, status: 1}},
  {key: {email: 1}, unique: true}
]

// Ver tamanho dos índices
db.transacoes.stats().indexSizes
```

### Índices Inúteis

```javascript
// ❌ Índice inútil: Superposto por composto
db.clientes.createIndex({cpf: 1})
db.clientes.createIndex({cpf: 1, nome: 1})  // O primeiro é redundante

// Remover
db.clientes.dropIndex({cpf: 1})

// ❌ Índice inútil: Selectividade baixa
db.clientes.createIndex({tipo: 1})  // Apenas PF/PJ (2 valores)
// 50% dos documentos têm o mesmo valor

// Melhor
db.clientes.createIndex({tipo: 1, cpf: 1})  // Composto é mais útil
```

## 5.2 - Connection Pooling

Conexões com MongoDB são caras. Reutilize-as:

```javascript
// ✓ CORRETO: Criar pool na inicialização
const { MongoClient } = require('mongodb');

const client = new MongoClient(
  'mongodb+srv://username:password@cluster.mongodb.net/',
  {
    maxPoolSize: 100,    // Máximo 100 conexões
    minPoolSize: 10,     // Mínimo 10 mantidas quentes
    maxIdleTimeMS: 60000 // Fechar após 60s inativo
  }
);

const db = client.db('banco_producao');

// ✓ Reutilizar conexões
app.get('/cliente/:id', async (req, res) => {
  const cliente = await db.collection('clientes').findOne({_id: req.params.id});
  res.json(cliente);
});

// Nunca fechar client() até aplicação encerrar
process.on('exit', () => client.close());
```

## 5.3 - Batching e Bulk Operations

```javascript
// ❌ LENTO: Múltiplas operações individuais
for (let i = 0; i < 10000; i++) {
  db.clientes.insertOne({nome: `Cliente ${i}`});  // 10.000 round-trips!
}

// ✓ RÁPIDO: Batch
const docs = [];
for (let i = 0; i < 10000; i++) {
  docs.push({nome: `Cliente ${i}`});
}
db.clientes.insertMany(docs);  // 1 round-trip!

// ✓ MUITO RÁPIDO: Bulk
const bulk = db.clientes.initializeUnorderedBulkOp();
for (let i = 0; i < 10000; i++) {
  bulk.insert({nome: `Cliente ${i}`});
}
bulk.execute();
```

Performance típica:
- Inserções individuais: 10.000 docs = 30+ segundos
- insertMany: 10.000 docs = 0.5 segundos (60x mais rápido!)
- bulk: 10.000 docs = 0.3 segundos (100x mais rápido!)

## 5.4 - Projeção para Economia de Banda

```javascript
// ❌ WASTEFUL: Recuperar campo gigante que não precisa
db.clientes.find({})  // Cada documento tem 10MB de histórico!

// ✓ EFICIENTE: Projetar apenas campos necessários
db.clientes.find(
  {},
  {nome: 1, email: 1, saldo: 1, _id: 0}  // 50KB por documento
)
```

Se você tiver 1 milhão de clientes:
- Sem projeção: 10 GB de dados transferidos ✗
- Com projeção: 50 MB de dados transferidos ✓

## 5.5 - Caching: Padrão Cliente + MongoDB

```javascript
// ✓ Cache-aside pattern
async function getCliente(clienteId) {
  // 1. Verificar cache (Redis/memcached)
  let cliente = await redisClient.get(`cliente:${clienteId}`);
  if (cliente) return JSON.parse(cliente);
  
  // 2. Se não em cache, fetch de MongoDB
  cliente = await db.collection('clientes').findOne({_id: clienteId});
  
  // 3. Armazenar em cache por 1 hora
  await redisClient.setex(`cliente:${clienteId}`, 3600, JSON.stringify(cliente));
  
  return cliente;
}

// ✓ Invalidar cache quando cliente muda
async function atualizarCliente(clienteId, updates) {
  await db.collection('clientes').updateOne({_id: clienteId}, {$set: updates});
  await redisClient.del(`cliente:${clienteId}`);  // Invalidar
}
```

## 5.6 - Write Concern para Durabilidade

```javascript
// Cenário: Você está processando transferência bancária

// ❌ RÁPIDO MAS ARRISCADO
db.transacoes.insertOne(
  {cliente_id: X, valor: 1000, tipo: "transferencia"},
  {writeConcern: {w: 1}}  // OK após PRIMARY confirmar
)
// Servidor cai 1 segundo depois... Dados perdidos!

// ✓ SEGURO (Default em Atlas)
db.transacoes.insertOne(
  {cliente_id: X, valor: 1000, tipo: "transferencia"},
  {writeConcern: {w: "majority"}}  // Aguarde maioria de réplicas
)
// Precisa de maioria das réplicas confirmar. Mais lento, mas seguro.

// ✓ MAIS SEGURO COM DURABILIDADE
db.transacoes.insertOne(
  {cliente_id: X, valor: 1000, tipo: "transferencia"},
  {writeConcern: {w: "majority", j: true}}  // E journal em disco
)
```

## 5.7 - Transactions para Operações Críticas

```javascript
// ✓ Transferência atomicamente
const session = client.startSession();
try {
  session.startTransaction();
  
  // Débito
  await db.collection('contas').updateOne(
    {_id: contaOrigem},
    {$inc: {saldo: -1000}},
    {session}
  );
  
  // Crédito
  await db.collection('contas').updateOne(
    {_id: contaDestino},
    {$inc: {saldo: +1000}},
    {session}
  );
  
  // Registrar transação (log de auditoria)
  await db.collection('transacoes').insertOne(
    {cliente_id: X, tipo: "transferencia", valor: 1000, status: "processada"},
    {session}
  );
  
  // Tudo commita junto
  await session.commitTransaction();
} catch (err) {
  await session.abortTransaction();
  console.error("Transferência falhou:", err);
} finally {
  await session.endSession();
}
```

## 5.8 - Esquema Validation para Consistência

```javascript
// ✓ Enforçar schema na escrita
db.createCollection("contas", {
  validator: {
    $jsonSchema: {
      bsonType: "object",
      required: ["_id", "cliente_id", "numero", "tipo", "saldo"],
      properties: {
        _id: {bsonType: "objectId"},
        cliente_id: {bsonType: "string"},
        numero: {bsonType: "string", minLength: 7, maxLength: 20},
        tipo: {enum: ["corrente", "poupanca", "investimento"]},
        saldo: {bsonType: "decimal"},
        ativa: {bsonType: "bool"},
        criada_em: {bsonType: "date"}
      },
      additionalProperties: false  // Rejeitar campos extras
    }
  }
})
```

## 5.9 - Monitoring: Queries Lentas

```javascript
// ✓ Profiler: Registrar queries lentas
db.setProfilingLevel(1, {slowms: 100})  // Log queries > 100ms

// Ver queries lentas
db.system.profile.find({millis: {$gt: 100}}).sort({ts: -1}).limit(10)

// Resultado mostra queryPlanner, executionStats, etc
{
  "op": "query",
  "ns": "banco.transacoes",
  "command": {find: "transacoes", filter: {cliente_id: X}},
  "millis": 250,  // ← LENTA!
  "executionStats": {
    "executionStages": {
      "stage": "COLLSCAN",  // ← Problema: full scan
      "nReturned": 1
    }
  }
}
```

## 5.10 - Shard Key: Decisão Crítica

Se você vai shardear, escolha o shard key com cuidado:

```javascript
// ✓ BOM: CPF (uniforme, imutável)
sh.shardCollection("banco.clientes", {cpf: 1})

// ✓ BOM: UUID aleatório
sh.shardCollection("banco.eventos", {event_id: 1})

// ❌ RUIM: Status (apenas 3 valores)
sh.shardCollection("banco.clientes", {status: 1})
// Resultado: Todos "ativos" vão para Shard 1, "inativo" para Shard 2
// Totalmente desbalanceado!

// ❌ RUIM: Timestamp (monotônico crescente)
sh.shardCollection("banco.transacoes", {data: 1})
// Resultado: Novas transações sempre vão para último shard
// Sobrecarrega shard mais novo, outros ficam ociosos

// ✓ MELHOR para time-series: Composto
sh.shardCollection("banco.transacoes", {cliente_id: 1, data: 1})
// Dados distribuídos por cliente, ordenados por data dentro de cada shard
```

## 5.11 - Query Performance: Checks

Antes de colocar em produção:

```javascript
// 1. Verificar se query usa índice
db.clientes.find({cpf: "111.222.333-44"}).explain("executionStats")
// "stage": "IXSCAN" ✓ ou "COLLSCAN" ✗

// 2. Verificar quantidade de documentos scaneados
{
  "executionStats": {
    "nReturned": 1,
    "totalDocsExamined": 1,  // ← Deve ser próximo de nReturned
    "executionStages": {"stage": "IXSCAN"}
  }
}

// 3. Verificar time
"executionTimeMillis": 1  // < 100ms é ideal
```

## 5.12 - Segurança: Autenticação e Autorização

```javascript
// ✓ MongoDB com autenticação
const client = new MongoClient(
  'mongodb+srv://user:password@cluster.mongodb.net/',
  {
    authSource: 'admin',  // Database de autenticação
    authMechanism: 'SCRAM-SHA-256'  // Mecanismo seguro
  }
);

// ✓ Criar user com role específico
db.createUser({
  user: "app_user",
  pwd: "strongPassword123!",
  roles: [
    {role: "readWrite", db: "banco_producao"},
    {role: "read", db: "banco_analytics"}  // Acesso limitado
  ]
})

// Agora app_user só pode:
// - read/write em banco_producao
// - read em banco_analytics
// - Não pode criar databases, alterar usuários, etc
```

---

# 🏦 MÓDULO 6: Simulação de Casos Bancários e Conformidade
**Duração: 25 minutos | Palavras: ~3000**

## Abertura

MongoDB é versátil, mas para o mercado Bancário do Brasil, alguns casos de uso são mais críticos que outros. Neste módulo, exploraremos aplicações específicas de serviços financeiros, conformidade regulatória, e como MongoDB resolve desafios únicos de banking.

## 6.1 - Caso de Uso 1: Detecção de Fraude

**Requisito**: Identificar padrões fraudulentos em tempo real.

```javascript
// Estrutura de dados para fraude
{
  _id: ObjectId(...),
  cliente_id: "CPF123",
  transacao_id: "TXN456",
  valor: Decimal128("50000"),
  data: ISODate("2024-01-15T10:00:00Z"),
  tipo: "saque",
  localizacao: {tipo: "Point", coordinates: [-23.5505, -46.6333]},  // São Paulo
  dispositivo: "iPhone13",
  ip: "191.234.23.111",
  risco: 0.95,  // 0-1 score de risco
  motivo_risco: ["saque_grande", "novo_dispositivo", "novo_ip", "localizacao_diferente"],
  status: "bloqueado"
}
```

**Índices críticos**:

```javascript
// Encontrar transações suspeitosas por cliente em tempo real
db.transacoes_fraude.createIndex({cliente_id: 1, data: -1, risco: -1})

// Geolocation search (cliente nunca transacionou em SP, mas transação é em SP)
db.transacoes_fraude.createIndex({localizacao: "2dsphere"})

// TTL: Deletar alertas resolvidos após 30 dias
db.alertas_fraude.createIndex({criado_em: 1}, {expireAfterSeconds: 2592000})
```

**Query em tempo real**:

```javascript
// Detectar padrões suspeitos
db.transacoes.aggregate([
  {$match: {cliente_id: "CPF123", data: {$gte: ISODate("2024-01-14")}}},
  {$group: {
    _id: "$cliente_id",
    num_transacoes: {$sum: 1},
    valor_total: {$sum: "$valor"},
    localizacoes: {$addToSet: "$localizacao"},
    dispositivos: {$addToSet: "$dispositivo"}
  }},
  {$match: {
    num_transacoes: {$gt: 10},  // Mais de 10 transações em 24h
    valor_total: {$gt: Decimal128("100000")}  // Mais de 100k
  }}
])
```

## 6.2 - Caso de Uso 2: KYC (Know Your Customer)

**Requisito**: Manter histórico de verificação e conformidade de cada cliente.

```javascript
{
  _id: "CPF123",
  nome: "João Silva",
  kyc_status: "verificado",
  kyc_nivel: 3,  // 1=básico, 2=intermediário, 3=completo
  verificacoes: [
    {
      data: ISODate("2020-01-15"),
      tipo: "documento",
      documento: "RG",
      numero: "123456789",
      validade: ISODate("2030-01-15"),
      status: "aprovado"
    },
    {
      data: ISODate("2020-01-16"),
      tipo: "biometria",
      status: "aprovado",
      score: 0.99
    },
    {
      data: ISODate("2023-01-15"),
      tipo: "atualizacao_endereço",
      status: "aprovado",
      endereco_anterior: "Rua A",
      endereco_novo: "Av. Paulista 1000"
    }
  ],
  pep_status: false,  // Pessoa Politicamente Exposta?
  aml_status: "limpo",  // Anti-Money Laundering check
  conformidade_gdpr: true,  // Consentimento GDPR?
  atualizado_em: ISODate("2024-01-15")
}
```

**Índices críticos**:

```javascript
// Encontrar clientes que precisam re-verificação
db.clientes.createIndex({kyc_status: 1, verificacoes: 1})

// Encontrar PEPs ou AML flags
db.clientes.createIndex({pep_status: 1, aml_status: 1})
```

**Compliance check**:

```javascript
// Clientes que não foram verificados em mais de 1 ano
db.clientes.find({
  atualizado_em: {$lt: ISODate("2023-01-15")},
  kyc_status: "verificado"
})
// → Enviar para re-verificação

// Clientes PEP que fazem transações grandes
db.transacoes.aggregate([
  {$match: {valor: {$gt: Decimal128("10000")}}},
  {$lookup: {
    from: "clientes",
    localField: "cliente_id",
    foreignField: "_id",
    as: "cliente"
  }},
  {$match: {"cliente.pep_status": true}},
  {$project: {cliente_id: 1, valor: 1, cliente_nome: "$cliente.nome"}}
])
// → Flag para investigação manual
```

## 6.3 - Caso de Uso 3: Histórico de Transações

**Requisito**: Auditoria completa de todos os movimentos.

```javascript
{
  _id: ObjectId(...),
  cliente_id: "CPF123",
  tipo: "transferencia",
  valor: Decimal128("5000.00"),
  moeda: "BRL",
  conta_origem: "123456-7",
  conta_destino: "654321-9",
  data: ISODate("2024-01-15T10:30:00Z"),
  status: "processada",
  tempo_processamento_ms: 245,
  descricao: "Transferência para amigo",
  referencia: "TXN20240115001",
  
  // Auditoria
  usuario_id: "USER456",
  ip_origem: "191.234.23.111",
  dispositivo: "iPhone13",
  canal: "mobile_app",
  
  // Regulatória
  cbr_code: "20.041",  // Código BC do Brasil
  notificado_bc: true,
  notificado_em: ISODate("2024-01-15T10:35:00Z")
}
```

**Índices críticos**:

```javascript
// Encontrar transações por cliente em período
db.transacoes.createIndex({cliente_id: 1, data: -1})

// Encontrar transações não notificadas ao BC
db.transacoes.createIndex({notificado_bc: 1, data: 1})

// TTL para deletar logs antigos (7 anos por lei)
db.transacoes_logs.createIndex(
  {data: 1},
  {expireAfterSeconds: 220752000}  // 7 anos
)
```

**Query de auditoria**:

```javascript
// Encontrar todas as transações de um cliente em uma data
db.transacoes.find({
  cliente_id: "CPF123",
  data: {
    $gte: ISODate("2024-01-01T00:00:00Z"),
    $lt: ISODate("2024-01-02T00:00:00Z")
  }
}).sort({data: 1})

// Resultado: Trace completo do dia do cliente
```

## 6.4 - Caso de Uso 4: Perfil de Cliente e Preferências

**Requisito**: Personalizar ofertas, taxas, e limites baseado em perfil.

```javascript
{
  _id: "CPF123",
  nome: "João Silva",
  email: "joao@email.com",
  
  // Perfil
  segmento: "premium",  // bronze, prata, ouro, premium
  score_crediticio: 850,
  idade: 35,
  profissao: "Engenheiro",
  renda_anual: Decimal128("180000"),
  
  // Comportamento
  dias_cliente: 1500,
  num_transacoes_mes: 45,
  gasto_medio_mes: Decimal128("15000"),
  saldo_total: Decimal128("250000"),
  
  // Produtos
  produtos: ["conta_corrente", "cartao_credito", "investimentos", "seguros"],
  limite_credito: Decimal128("50000"),
  taxa_juro: 0.025,  // 2.5% aa (premium)
  
  // Preferências
  preferencias: {
    comunicacoes: "email",
    notificacoes: ["saque", "deposito", "transacao_grande"],
    limite_notificacao: Decimal128("5000"),
    idioma: "pt-BR",
    marketing: true
  },
  
  // Ofertas ativas
  ofertas: [
    {codigo: "OFERTA001", descricao: "Investimento sem taxa", expira_em: ISODate("2024-12-31")},
    {codigo: "OFERTA002", descricao: "Cartão com cashback", expira_em: ISODate("2024-06-30")}
  ]
}
```

**Índices**:

```javascript
// Encontrar clientes premium para oferta especial
db.clientes.createIndex({segmento: 1, saldo_total: -1})

// Encontrar clientes em risco de churn
db.clientes.createIndex({dias_cliente: 1, num_transacoes_mes: -1})
```

## 6.5 - GDPR: Right to be Forgotten

```javascript
// ✓ GDPR: Direito ao esquecimento
async function deletarClienteGDPR(clienteId) {
  const session = client.startSession();
  try {
    session.startTransaction();
    
    // 1. Anonimizar dados pessoais do cliente
    await db.collection('clientes').updateOne(
      {_id: clienteId},
      {$set: {
        nome: "[DELETADO]",
        email: "[DELETADO]",
        cpf: "[DELETADO]",
        status: "deletado_gdpr",
        deletado_em: new Date()
      }},
      {session}
    );
    
    // 2. Manter apenas IDs para auditoria (exigido por lei)
    await db.collection('auditoria_gdpr').insertOne({
      cliente_id_hash: hashMD5(clienteId),
      data_delecao: new Date(),
      motivo: "GDPR - Right to be forgotten"
    }, {session});
    
    // 3. NÃO deletar transações (auditoria exigida por lei)
    // Apenas anular identificação pessoal
    
    await session.commitTransaction();
  } catch (err) {
    await session.abortTransaction();
    throw err;
  }
}
```

## 6.6 - Conformidade: Encriptação de Dados Sensíveis

```javascript
// ✓ Queryable Encryption: Criptografar dados sensíveis mas ainda poder fazer queries
const {ClientEncryption} = require('mongodb-client-encryption');

const clientEncryption = new ClientEncryption({
  keyVaultClient: client,
  keyVaultNamespace: "encryption.keys",
  kmsProviders: {aws: {...}}  // AWS KMS para chaves mestres
});

// Dados sensíveis (CPF, cartão) são criptografados
{
  _id: "CPF123",
  nome: "João Silva",
  cpf: "<encrypted>A1B2C3D4E5F6G7H8...</encrypted>",  // Criptografado
  cartao: "<encrypted>B2C3D4E5F6G7H8I9...</encrypted>"
}

// Mas ainda posso fazer queries!
db.clientes.find({cpf: {$eq: clientEncryption.encrypt("111.222.333-44")}})
// MongoDB decripta no lado do cliente automaticamente
```

## 6.7 - Conformidade: Audit Logging

```javascript
// ✓ Registrar TUDO para auditoria
db.createCollection("audit_log", {
  validator: {
    $jsonSchema: {
      bsonType: "object",
      required: ["timestamp", "usuario_id", "acao", "colecao", "documento_id"],
      properties: {
        timestamp: {bsonType: "date"},
        usuario_id: {bsonType: "string"},
        acao: {enum: ["INSERT", "UPDATE", "DELETE", "READ"]},
        colecao: {bsonType: "string"},
        documento_id: {bsonType: "string"},
        antes: {bsonType: "object"},  // Valores antigos
        depois: {bsonType: "object"},  // Valores novos
        ip: {bsonType: "string"},
        resultado: {enum: ["sucesso", "falha"]},
        motivo_falha: {bsonType: "string"}
      }
    }
  }
})

// TTL: Manter por 5 anos (lei exige)
db.audit_log.createIndex(
  {timestamp: 1},
  {expireAfterSeconds: 157680000}  // 5 anos
)
```

## 6.8 - Compliance: Teste de Cenários

```javascript
// Cenário 1: Detecção de Lavagem de Dinheiro (AML)
// Múltiplas transferências rápidas para contas diferentes
db.transacoes.aggregate([
  {$match: {
    cliente_id: "CPF123",
    tipo: "transferencia",
    data: {$gte: ISODate("2024-01-15T00:00:00Z")}
  }},
  {$group: {
    _id: "$cliente_id",
    num_contas_destino: {$addToSet: "$conta_destino"},
    total_transferencias: {$sum: "$valor"}
  }},
  {$match: {
    "num_contas_destino": {$size: {$gt: 5}}  // Mais de 5 contas
  }}
])

// Cenário 2: Transação Estruturada (Smurfing)
// Múltiplas transações pequenas para evitar reportagem
db.transacoes.aggregate([
  {$match: {
    cliente_id: "CPF123",
    valor: {$gte: Decimal128("5000"), $lte: Decimal128("9999")},  // Abaixo do threshold
    data: {$gte: ISODate("2024-01-01")}
  }},
  {$group: {
    _id: "$cliente_id",
    num_transacoes: {$sum: 1},
    total: {$sum: "$valor"}
  }},
  {$match: {
    num_transacoes: {$gt: 10},  // Muitas transações
    total: {$gt: Decimal128("100000")}  // Total grande
  }}
])
```

---

# 📚 MÓDULO 7: Recursos, Comunidade e Evolução
**Duração: 25 minutos | Palavras: ~3000**

## Abertura

Você agora tem conhecimento para trabalhar com MongoDB em produção. Mas a tecnologia evolui constantemente. Neste módulo, exploraremos recursos para aprendizado contínuo, o ecossistema MongoDB, e o que esperar do futuro.

## 7.1 - Recursos Oficiais

### MongoDB University (Gratuito)

**mongodb.com/university**

Cursos estruturados:

- **M0**: MongoDB Basics (iniciantes, ~4 horas)
- **M001**: MongoDB Basics (mais profundo, ~10 horas)
- **M220J/N/P**: Backend Development with MongoDB (linguagem específica)
- **M320**: Data Modeling (essencial para design)
- **M201**: MongoDB Performance (índices, otimização)
- **M121**: Aggregation Pipeline
- **M320**: Data Governance

Cada curso inclui vídeos, exercícios práticos, e certificado.

### Documentação Oficial

**docs.mongodb.com**

A documentação MongoDB é exemplar—entre as melhores da indústria.

- **Manual**: Explicação de cada conceito
- **Driver Documentation**: Por linguagem (Node, Python, Java, Go, C#)
- **Tutorial**: Passo-a-passo para tarefas comuns
- **Reference**: Sintaxe exata de todos os operadores

### MongoDB Atlas Free Tier

**mongodb.com/cloud/atlas**

Cluster gratuito de 512MB:

- Perfeito para learning
- Inclui backup automático
- Acesso a recursos de monitoring básicos
- Multi-cloud (AWS, Google Cloud, Azure)

## 7.2 - Drivers Oficiais

MongoDB mantém drivers oficiais para praticamente toda linguagem:

### Node.js Driver

```javascript
// npm install mongodb
const {MongoClient} = require('mongodb');
const client = new MongoClient('mongodb+srv://...');
```

Popular ORM: Mongoose, Prisma

### Python Driver (PyMongo)

```python
# pip install pymongo
from pymongo import MongoClient
client = MongoClient('mongodb+srv://...')
```

Popular ORM: MongoEngine, Motor (async)

### Java Driver

```java
// Maven: org.mongodb:mongodb-driver-sync
MongoClient mongoClient = MongoClients.create(uri);
```

Popular ORM: Spring Data MongoDB

### Go Driver

```go
// go get go.mongodb.org/mongo-driver
client, err := mongo.Connect(context.Background(), options.Client().ApplyURI(uri))
```

### C# Driver

```csharp
// NuGet: MongoDB.Driver
var client = new MongoClient(uri);
```

Todos os drivers oferecem:
- Connection pooling automático
- Async/await support
- Type safety
- Comprehensive documentation

## 7.3 - Comunidade: Onde Obter Ajuda

### MongoDB Community Forums

**developer.mongodb.com/community**

Fórum oficial com milhares de threads. Respostas de MongoDB engineers e comunidade.

### Stack Overflow

**stackoverflow.com** tag: `mongodb`

12.000+ perguntas respondidas. Busque sempre aqui primeiro.

### Reddit

**/r/mongodb**

Comunidade ativa, dicas práticas, troubleshooting.

### MongoDB.Local Events

Conferências em várias cidades (incluindo Brasil):

- Palestra técnicas
- Hands-on labs
- Networking com outros usuários
- Anúncios de features novas

## 7.4 - Ferramentas Auxiliares

### MongoDB Compass

**mongodb.com/products/compass**

GUI profissional para MongoDB:

- Browse dados visualmente
- Executar queries
- Análise de índices
- Explain plan visual

### mongosh (MongoDB Shell)

O novo shell interativo (substitui mongo):

```javascript
mongosh "mongodb+srv://..."
> db.clientes.find({cpf: "111.222.333-44"})
```

### MongoDB VSCode Extension

Integração no VSCode:

- Autocomplete para queries
- Syntax highlighting
- Executar direto no editor

## 7.5 - Roadmap 2025-2026

Segundo MongoDB Blog (Dec 2024), as inovações esperadas:

### 1. Native Vector Indexing

Atualmente Atlas Vector Search é separado. Em 2025, Vector Search será integrado no core:

```javascript
// 2025+: Indexing nativo
db.embeddings.createIndex({vector: "vector"})
```

Benefícios: Performance 10x melhor, menores custos.

### 2. Temporal Queries

Suporte nativo para dados históricos:

```javascript
// Encontrar valor de saldo em uma data específica
db.saldo_historico.temporal_find({
  data: ISODate("2024-01-15"),
  cliente_id: "CPF123"
})
```

### 3. Machine Learning Integration

MongoDB oferecerá ML Models rodando directly no MongoDB:

```javascript
// Treinar modelo de fraude direto no MongoDB
db.transacoes.train_model({
  type: "fraud_detection",
  features: ["valor", "localizacao", "dispositivo"]
})
```

### 4. Stream Processing

Processamento de eventos em tempo real nativo:

```javascript
// Criar stream de eventos
db.createStream("transacoes", {
  processor: "fraud_detector",
  output_collection: "transacoes_fraude"
})
```

### 5. Cost Optimization

Autoscaling dinâmico e redução de custos:

- Compute autoscaling (processar menos em baixa demanda)
- Storage tier optimization (dados quentes vs. frios)

## 7.6 - MongoDB 8.0: O Que Mudou

Lançado em Outubro 2024, MongoDB 8.0 é a versão mais significativa em anos:

### Performance

- **36% mais rápido** em reads
- **59% mais rápido** em writes
- Nova arquitetura de storage

### Queryable Encryption

Range queries em dados criptografados:

```javascript
// Antes: Range queries não funcionavam em dados criptografados
db.clientes.find({saldo: {$gt: Decimal128("1000")}})  // ❌ Não funciona se criptografado

// 8.0+: Range queries funcionam!
db.clientes.find({saldo: {$gt: Decimal128("1000")}})  // ✓ Funciona com Queryable Encryption
```

### Clustered Collections

Organizar documentos em disco por índice cluster para performance:

```javascript
db.createCollection("transacoes", {
  clusteredIndex: {key: {cliente_id: 1}, unique: false}
})
```

### Atlas Advisor

IA que recomenda otimizações automaticamente:

- Índices que deveria ter
- Índices desnecessários
- Dados que deveria arquivar

## 7.7 - Integração com IA/ML

MongoDB está se posicionando como banco de dados para AI:

### Vector Embeddings

Armazenar embeddings de modelos como GPT-4:

```javascript
{
  _id: ObjectId(...),
  cliente_id: "CPF123",
  descricao: "Cliente com alto risco de fraude",
  embedding: [0.123, -0.456, 0.789, ...]  // Vetor de 1536 dimensões
}

// Vector search
db.profiles.find({
  embedding: {
    $near: {vector: queryVector, k: 10}
  }
})
```

### Atlas AI

Agentes de IA que consultam MongoDB automaticamente:

```
User: "Qual é o saldo total de todos meus clientes premium?"
↓
Atlas AI interprets
↓
db.clientes.aggregate([
  {$match: {segmento: "premium"}},
  {$group: {_id: null, total: {$sum: "$saldo"}}}
])
↓
Atlas AI returns: "Total de R$ 2.3 bilhões"
```

## 7.8 - Tendências de Mercado

### Adoção em Enterprise

- Fortune 500: 70%+ usa MongoDB
- Serviços Financeiros: Crescimento acelerado
- Brasil: Nubank, Banco Inter, e dezenas de fintechs usam MongoDB

### Comparação com Alternativas

| Aspecto | MongoDB | PostgreSQL | DynamoDB | Firestore |
|---------|---------|------------|----------|-----------|
| Schema Flexível | ✓ | ~ | ✓ | ✓ |
| ACID | ✓ | ✓ | ✗ | ~ |
| Horizontal Scale | ✓ | ~ | ✓ | ✓ |
| Vector Search | ✓ | ~ | ✗ | ✗ |
| Multi-cloud | ✓ | ~ | ✗ (AWS) | ✗ (Google) |
| Custo | ~ | Baixo | Alto | Alto |

---

# 🎯 MÓDULO 8: Discussão Prática e Próximos Passos
**Duração: 25 minutos | Palavras: ~2500**

## Abertura

Completamos a trajetória técnica completa do MongoDB. Agora é hora de trazer para a realidade dos Bancos do Brasil: como implementar? Quais desafios enfrentaremos? Como minimizar riscos?

## 8.1 - Implementação: Roadmap Realista

### Fase 1: Avaliação (Semanas 1-4)

```
Atividades:
- Criar cluster MongoDB Atlas gratuito (1 dia)
- Design primeiro modelo de dados (3-4 dias)
- PoC com dados reais da sua empresa (1-2 semanas)
- Benchmark: MongoDB vs MySQL em seu dataset (1 semana)

Métricas de Sucesso:
- MongoDB 30%+ mais rápido que MySQL? ✓ Prosseguir
- Queries complexas simplificadas? ✓ Prosseguir
- Equipe consegue trabalhar com MongoDB? ✓ Prosseguir

Timeline: 1 mês
Custo: $0 (Atlas free tier + dev time)
```

### Fase 2: MVP (Meses 2-4)

```
Atividades:
- Implementar 1 serviço NÃO-crítico em MongoDB
  (Exemplo: Sistema de Recomendações de Produtos)
- Configurar replicação (3 nodes mínimo)
- Implementar monitoring e alertas
- Treinar equipe em operações
- Stress test: 100% da carga esperada

Métricas de Sucesso:
- 99.9% uptime em staging
- Latência p99 < 100ms
- Falha de 1 node = failover automático < 30s

Timeline: 3 meses
Custo: ~$2000/mês (small cluster Atlas)
```

### Fase 3: Integração Maior (Meses 5-8)

```
Atividades:
- Migrar Customer Data Platform para MongoDB
- Integrar com fraud detection
- Integrar com analytics
- Compliance audit completo

Métricas de Sucesso:
- Passou em compliance check ✓
- ROI positivo comparado a SQL ✓
- Equipe confiante em operações ✓

Timeline: 4 meses
Custo: ~$10.000/mês (production cluster)
```

### Fase 4: Migração Crítica (Meses 9-12)

```
Atividades:
- Considerar migração de dados críticos (opcional)
- Ou: Manter SQL + MongoDB lado-a-lado
- Hybrid approach é comum em bancos

Decisão: Full MongoDB? Hybrid? Dual-write? 
Depende de resultados da Fase 3.
```

## 8.2 - Riscos e Mitigação

### Risco 1: Shard Key Ruim

**Risco**: Escolher shard key errado causa desbalanceamento de dados.

**Mitigação**:
- Consultar MongoDB professional services
- Simular padrão de acesso antes de shard
- Monitorar distribuição após sharding

### Risco 2: Índices Ineficientes

**Risco**: Índices ruins causam queries lentas.

**Mitigação**:
- Usar MongoDB Atlas Advisor para recomendações
- Rodar teste de carga com real data
- Profile queries em staging

### Risco 3: Consumo de Memória

**Risco**: Dados crescem e não cabem em RAM.

**Mitigação**:
- Arquitetura de cache (Redis + MongoDB)
- Sharding para distribuir dados
- TTL indexes para limpar dados antigos

### Risco 4: Conformidade Regulatória

**Risco**: Banco de dados não atende requisitos de auditoria.

**Mitigação**:
- MongoDB é SOC 2, ISO 27001, HIPAA, PCI-DSS certificado
- Queryable Encryption para LGPD
- Audit logging obrigatório desde o dia 1

## 8.3 - Comparação Financeira: SQL vs MongoDB

```
Cenário: 1 TB de dados, 10.000 req/s, alta disponibilidade

SQL Relacional (PostgreSQL):
- Infraestrutura: Servidor grande ($50k/ano)
- 2 replicas em standby ($100k/ano)
- DBA de tempo integral ($150k/ano)
- Disaster recovery customizado ($20k/ano)
- TOTAL: ~$320k/ano

MongoDB Atlas:
- Managed database service ($120k/ano)
- Backup automático (included)
- Monitoring automático (included)
- Multi-region replication (included)
- Serverless option para picos (pay-per-op)
- TOTAL: ~$120k/ano

Economia: $200k/ano (62% redução!)
```

## 8.4 - Desafios Culturais

### Desafio 1: Equipe Acostumada com SQL

**Solução**:
- Treinamento estruturado (MongoDB University)
- Certificações (M201, M320)
- Documentação interna de padrões
- Code reviews com especialistas

### Desafio 2: "MongoDB Não é Enterprise"

**Realidade**:
- Nubank (maior fintech do Brasil) usa MongoDB
- NatWest (banco britânico) processa 150.000 transações/seg em MongoDB
- MongoDB serve 60.000+ organizações, 70% da Fortune 100

### Desafio 3: "Precisamos de Garantias ACID"

**Realidade**:
- MongoDB 4.0+ (2018+) tem transações ACID distribuídas
- Transações multi-documento
- Isolamento completo

## 8.5 - Decisão Final: Hybrid vs Full MongoDB

Para o mercado Bancário do Brasil, recomendo abordagem **Hybrid**:

### O Que Fica em SQL
- Serviços core extremamente críticos (raríssima alteração de schema)
- Relatórios OLAP complexos (data warehouse)
- Dados estruturados fixos (tabela de taxas)

### O Que Vai para MongoDB
- Dados de cliente (schema evolui frequentemente)
- Transações e histórico (volume crescente)
- Fraude detection (queries analíticas)
- Recomendações e personalizações (flexível)
- Change events (event sourcing)

**Vantagem**: Melhor dos dois mundos, risco minimizado.

## 8.6 - Plano de Ação Imediato (Próximas 2 Semanas)

### Semana 1

```
Day 1:
- Designar MongoDB champion (1 pessoa)
- Criar grupo de trabalho (5-8 pessoas)

Day 2-3:
- Cada pessoa segue M001 do MongoDB University
- Discute padrões de modelagem

Day 4-5:
- Criar cluster gratuito no Atlas
- Importar 1GB de dados reais da sua empresa
- Comparar queries: SQL vs MongoDB
```

### Semana 2

```
Day 6-7:
- Design de primeiro PoC (Fraud Detection)
- Estimar esforço e timeline

Day 8-9:
- Apresentar findings para stakeholders
- Decisão: Go/No-go para PoC

Day 10:
- Kick-off PoC se aprovado
```

## 8.7 - Mensuração de Sucesso

Após 6 meses, as métricas críticas devem ser:

1. **Performance**: MongoDB 2-5x mais rápido que SQL alternativa
2. **Custo**: Redução de 30%+ em infraestrutura + DBA
3. **Desenvolvimento**: Features novas levam 50% menos tempo
4. **Reliability**: 99.99% uptime (SLA atingido)
5. **Compliance**: Passou em todos os audits

Se 4 de 5 métricas forem atingidas → Sucesso ✓

## 8.8 - Recursos Internos da sua empresa

Sugestões para criar capacidade interna:

### Documentação Interna

Criar wiki/GitBook com:
- Padrões de design MongoDB para sua empresa
- Runbooks de operação
- Exemplos de código (Node + MongoDB)
- Guia de migrations
- FAQ e troubleshooting

### Training

- Trazer MongoDB consultant para workshop (2-3 dias)
- Certificar 5-10 pessoas em M201 (Performance)
- Certificar 5-10 pessoas em M320 (Data Modeling)

### Community

- Criar grupo interno de MongoDB
- Reuniões mensais para compartilhar learnings
- Participar em MongoDB.local Brasil (quando houver)

## 8.9 - Conclusão: Por Que usar MongoDB para o mercado Bancário do Brasil

1. **Escalabilidade**: De 10k para 10M transações/dia sem redesign
2. **Flexibilidade**: Produtos novos não exigem migration DBA
3. **Performance**: Latência baixa crítica para banking
4. **Conformidade**: Atende todas exigências regulatórias brasileiras
5. **Custo**: 60% menos infraestrutura com melhor performance
6. **Talento**: Devs jovens preferem MongoDB a SQL, facilita recrutamento
7. **Futuro**: IA/ML integrado é aposta do MongoDB

## 8.10 - Perguntas Esperadas na Discussão

### P: "E se o MongoDB ficar fora?"
R: Atlas tem SLA de 99.99% com multi-region replication. Além disso, dados críticos podem ficar em SQL como fallback.

### P: "Custo de treinamento?"
R: Cursos MongoDB University são gratuitos. Certificações são ~$150. Versus SQL expert = $200k/ano de consultoria.

### P: "E LGPD/GDPR?"
R: MongoDB suporta encryption, audit logging, e PITR. Atende requisitos completos.

### P: "Quanto tempo de POC?"
R: 4-6 semanas para resultado significativo. 3-6 meses para decisão go/no-go.

### P: "Não devemos completar todo o projeto no SQL primeiro?"
R: Risco de dead-end. SQL design de hoje pode ser errado amanhã. MongoDB permite iterar. Hybrid approach é melhor.

---

## 📊 RESUMO FINAL: Visualização dos 8 Módulos

```
Módulo 1 (20 min): POR QUE MongoDB existe?
    ↓ Entende motivação
Módulo 2 (25 min): COMO MongoDB funciona?
    ↓ Entende arquitetura
Módulo 3 (30 min): COMO estruturar dados?
    ↓ Entende design
Módulo 4 (35 min): COMO usar MongoDB?
    ↓ Entende sintaxe
Módulo 5 (35 min): COMO otimizar?
    ↓ Entende performance
Módulo 6 (25 min): COMO usar em Banking?
    ↓ Entende casos
Módulo 7 (25 min): ONDE aprender mais?
    ↓ Entende ecossistema
Módulo 8 (25 min): COMO implementar?
    ↓ Pronto para ação

TOTAL: 240 minutos = 4 horas ✓
```

---

## 📝 NOTAS FINAIS PARA O APRESENTADOR

### Dicas de Apresentação

1. **Mantenha energizado**: MongoDB é apaixonante. Deixe isso transparecer.

2. **Use exemplos reais**: Não conceitos abstratos. "Saque de R$ 50k" é melhor que "valor genérico".

3. **Mostre live**: Se possível, execute queries ao vivo no MongoDB Compass. Muito mais impactante.

4. **Pause estratégica**: Após conceitos pesados (Sharding, Aggregation), faça uma pausa.

5. **Relate com experiência deles**: "Vocês já tiveram problema de schema lock? MongoDB resolvia isso."

6. **Evite comparações negativas**: Não diga "SQL é ruim". Diga "MongoDB é melhor para este caso de uso específico".

7. **Reconheça limitações**: Honestidade gera confiança. "MongoDB não é ideal para data warehouse OLAP gigante."

### Interatividade

- **Polling**: "Quantos aqui já usaram NoSQL?" (Engaja)
- **Q&A**: Não deixe para final. Pause a cada módulo.
- **Hands-on**: Se possível, 15 min práticos em Módulo 8 (write simples, find, update)

### Timing

- Módulo 1: 20 min (história é rápida, engaja)
- Módulo 2: 25 min (fundamentals, pode ir rápido)
- Módulo 3: 30 min (design é o mais importante, vá devagar)
- Pausa de 10 min aqui (metade do treinamento)
- Módulo 4: 35 min (sintaxe, prático)
- Módulo 5: 35 min (otimização, profundo)
- Pausa de 10 min (final da tarde)
- Módulo 6: 25 min (simulação de casos reais, específico para empresas ficticias)
- Módulo 7: 25 min (recursos, não exija concentração, relaxado)
- Módulo 8: 25 min (prático, energético, conclusão)

### Recursos para Impressionar

- Números reais: NatWest processando 150k transações/seg
- Comparação financeira: 60% redução de custo vs SQL + DBA
- Benchmark live: Mostrar MongoDB 10x mais rápido em query específica
- Case study: Nubank + MongoDB