# 📊 Financial Analytics — Planejamento do Projeto

## 🎯 Objetivo

Desenvolver um projeto de **Data Analytics aplicado ao mercado financeiro**, utilizando dados históricos de diferentes ativos e indicadores financeiros para realizar uma análise de **risco, retorno e comportamento histórico dos investimentos**.

O projeto terá como objetivo inicial responder perguntas como:

> **Quais ativos e classes de ativos apresentaram historicamente a melhor relação entre retorno e risco?**

A partir dessa análise, será construído um **dashboard no Power BI**, acompanhado de um **storytelling baseado nos dados**, e posteriormente uma aplicação em **Streamlit** para disponibilizar a análise de forma interativa.

O projeto também evoluirá de uma primeira versão com processamento manual para um **pipeline automatizado utilizando Airflow**.

---

# 🗺️ Visão geral do projeto

```text
ETAPA 1
Busca por conhecimento
        ↓
ETAPA 2
Planejamento / Rota
        ↓
ETAPA 3
Mão na massa
        ↓
ETAPA 4
Subida de nível
        ↓
Projeto completo
```

### Evolução técnica

```text
Dados históricos
      ↓
Carga manual
      ↓
PostgreSQL
      ↓
ETL com Python
      ↓
Dados tratados
      ↓
Análise exploratória
      ↓
Indicadores financeiros
      ↓
Power BI
      ↓
Storytelling / README
      ↓
Automação com Airflow
      ↓
Extração automática
      ↓
Streamlit
```

---

# 1. 📚 Etapa 1 — Busca por conhecimento

## Objetivo

Antes de iniciar a implementação, compreender os principais conceitos necessários para desenvolver o projeto.

A etapa será dividida em duas frentes:

* Data Engineering / Airflow
* Financial Analytics

---

## 1.1. Airflow

Estudar como funciona o Apache Airflow e quais são os conceitos necessários para posteriormente utilizá-lo na automação do projeto.

### Conceitos a estudar

* O que é Airflow
* O que é um DAG
* Tasks
* Operators
* Scheduler
* Executor
* Dependencies
* Scheduling
* Retries
* Logs
* XCom
* Connections
* Variables / Secrets
* Execução periódica
* Estrutura de um projeto Airflow
* Docker + Airflow

### Objetivo prático

Ao final dessa etapa, ser capaz de compreender como transformar:

```text
Extração
   ↓
Tratamento
   ↓
Carga
```

em um pipeline orquestrado:

```text
              AIRFLOW
                 │
                 ↓
              Extract
                 ↓
              Transform
                 ↓
                Load
```

---

# 1.2. Análise financeira

Estudar os conceitos necessários para analisar historicamente diferentes ativos e estratégias de investimento.

## Classes de ativos

Inicialmente estudar quais classes fazem sentido para o projeto, por exemplo:

* Ações
* ETFs
* FIIs
* Renda fixa
* Índices
* Câmbio
* Outros ativos relevantes

A definição final dependerá da disponibilidade e qualidade dos dados.

---

## Indicadores

Estudar o significado, cálculo e interpretação dos principais indicadores.

### Retorno

* Retorno absoluto
* Retorno acumulado
* Retorno anualizado
* CAGR

### Risco

* Volatilidade
* Desvio padrão
* Maximum Drawdown

### Retorno ajustado ao risco

* Sharpe Ratio
* Outros indicadores que se mostrarem relevantes

### Relação entre ativos

* Correlação
* Beta

---

## Outros conceitos

Estudar também:

* Risco × retorno
* Diversificação
* Benchmark
* Inflação
* Taxa de juros
* Liquidez
* Dividendos
* Reinvestimento
* Custos
* Impostos
* Limitações de análises históricas

### Objetivo

Não apenas saber calcular os indicadores, mas conseguir responder:

> **O que esse indicador significa e qual informação ele fornece para a análise?**

---

# 2. 🧭 Etapa 2 — Rota

## Objetivo

Planejar a solução antes de iniciar a implementação.

A ideia é criar uma representação visual que permita entender:

* O que precisa ser feito;
* Quais componentes existem;
* Como eles se conectam;
* Quais dados entram e saem de cada etapa;
* Quais tecnologias serão utilizadas.

---

# 2.1. Mapa do projeto

Construir um mapa mental / fluxograma representando o caminho completo:

```text
                     FONTES DE DADOS
                           │
                           ↓
                    DADOS HISTÓRICOS
                           │
                           ↓
                      PostgreSQL
                           │
                           ↓
                          ETL
                           │
                           ↓
                    DADOS TRATADOS
                           │
              ┌────────────┴────────────┐
              ↓                         ↓
          SQL / Python              Power BI
              │                         │
              ↓                         ↓
          Indicadores              Dashboard
              │                         │
              └────────────┬────────────┘
                           ↓
                       INSIGHTS
                           │
                           ↓
                      Storytelling
                           │
                           ↓
                       GitHub
```

Posteriormente, com a automação:

```text
                     FONTE DE DADOS
                           │
                           ↓
                        AIRFLOW
                           │
                    ┌──────┴──────┐
                    ↓             ↓
                 Extract       Validação
                    │
                    ↓
                   ETL
                    │
                    ↓
               PostgreSQL
                    │
          ┌─────────┼─────────┐
          ↓         ↓         ↓
        SQL      Power BI  Streamlit
          │         │         │
          └─────────┼─────────┘
                    ↓
                 Análise
```

---

# 2.2. Planejamento das ferramentas

Definir durante essa etapa quais ferramentas serão utilizadas e qual será a responsabilidade de cada uma.

| Ferramenta   | Responsabilidade                             |
| ------------ | -------------------------------------------- |
| Python       | Extração, tratamento e análise               |
| PostgreSQL   | Armazenamento dos dados                      |
| SQL          | Consulta e análise dos dados                 |
| Airflow      | Orquestração do pipeline                     |
| Power BI     | Dashboard e visualização                     |
| Streamlit    | Aplicação interativa                         |
| Git / GitHub | Versionamento e documentação                 |
| Docker       | Avaliar necessidade para ambiente do projeto |

---

# 2.3. Organização das tarefas

Utilizar uma ferramenta de planejamento, como:

* GitHub Projects
* Miro
* draw.io / diagrams.net
* Mermaid
* Notion

O objetivo é transformar o projeto em tarefas menores e acompanhar sua evolução.

---

# 3. 🔨 Etapa 3 — Mão na massa

## Objetivo

Construir a primeira versão funcional do projeto utilizando inicialmente um processo **manual e controlado**.

A automação será deixada para a Etapa 4.

---

# 3.1. Extração dos dados históricos

Inicialmente, realizar a obtenção manual dos dados históricos necessários para a análise.

### Processo

```text
Fonte de dados
      ↓
Extração manual
      ↓
Arquivo / Dataset
      ↓
PostgreSQL
```

### Objetivo

Construir uma base histórica suficiente para realizar a análise e validar a metodologia antes de automatizar a coleta.

---

# 3.2. Banco de dados

Criar a estrutura inicial no PostgreSQL.

Separar conceitualmente:

```text
DADOS BRUTOS
     ↓
DADOS TRATADOS
```

Os dados originais devem ser preservados sempre que possível, permitindo reproduzir e validar o processo de tratamento.

---

# 3.3. ETL

Desenvolver um processo em Python para tratamento dos dados.

### Fluxo

```text
RAW DATA
   ↓
Extract
   ↓
Transform
   ├── Limpeza
   ├── Padronização
   ├── Tratamento de valores ausentes
   ├── Tratamento de tipos
   ├── Validação
   └── Cálculo / preparação de campos
   ↓
Load
   ↓
DADOS TRATADOS
```

Inicialmente, o processo será executado manualmente.

A automação será desenvolvida posteriormente com Airflow.

---

# 3.4. Análise exploratória

Com os dados tratados, realizar uma análise exploratória para compreender o comportamento dos ativos.

Investigar:

* Distribuição dos retornos;
* Evolução histórica;
* Períodos de alta e queda;
* Volatilidade;
* Drawdowns;
* Correlação;
* Diferenças entre classes de ativos;
* Comportamento em diferentes períodos.

---

# 3.5. Indicadores

Calcular os indicadores definidos durante a Etapa 1.

Exemplos:

```text
Retorno
Retorno acumulado
Retorno anualizado
CAGR
Volatilidade
Maximum Drawdown
Sharpe Ratio
Correlação
Beta
```

Os indicadores deverão ser interpretados, e não apenas calculados.

---

# 3.6. Definição do storytelling

A análise deverá responder perguntas claras.

Exemplos:

* Quais ativos apresentaram maior retorno?
* Quais apresentaram maior risco?
* Quais apresentaram melhor relação entre risco e retorno?
* Quais apresentaram maiores perdas históricas?
* Quais ativos apresentaram comportamento semelhante?
* O ativo de maior retorno também apresentou o melhor retorno ajustado ao risco?
* Os resultados mudam dependendo do período analisado?

O objetivo é transformar:

```text
DADOS
  ↓
INDICADORES
  ↓
ANÁLISE
  ↓
INSIGHTS
  ↓
CONCLUSÕES
```

---

# 3.7. Dashboard — Power BI

Depois que a análise estiver definida, criar o dashboard.

O dashboard deve ser consequência da análise, e não o contrário.

### Possível estrutura

#### Página 1 — Market Overview

* Principais indicadores
* Retorno
* Volatilidade
* Sharpe
* Drawdown

#### Página 2 — Comparação de ativos

* Retorno
* Risco
* Sharpe
* Comparação entre ativos

#### Página 3 — Performance histórica

* Evolução dos ativos
* Retorno acumulado
* Comparação temporal

#### Página 4 — Risco

* Volatilidade
* Drawdown
* Distribuição dos retornos
* Correlação

#### Página 5 — Insights

Apresentação dos principais resultados encontrados na análise.

---

# 3.8. Storytelling no README

O README deverá apresentar o projeto como uma análise completa.

Estrutura prevista:

```text
Contexto
   ↓
Pergunta
   ↓
Dados
   ↓
Metodologia
   ↓
Tratamento
   ↓
Indicadores
   ↓
Resultados
   ↓
Insights
   ↓
Dashboard
   ↓
Limitações
   ↓
Conclusão
```

---

# 3.9. Limitações

Documentar as limitações da análise.

Por exemplo:

* Resultados históricos não garantem resultados futuros;
* O período analisado pode influenciar significativamente as conclusões;
* Custos e impostos podem não estar contemplados em determinadas análises;
* Liquidez pode não ser considerada em todos os cenários;
* Dados históricos não representam necessariamente todas as condições futuras;
* Resultados podem sofrer influência da seleção dos ativos e do período analisado.

O objetivo é deixar claro que o projeto representa uma **análise histórica baseada em dados**, e não uma recomendação individual de investimento.

---

# 4. 🚀 Etapa 4 — Subida de nível

## Objetivo

Transformar o projeto manual em uma solução automatizada e disponibilizar a análise por meio de uma aplicação web.

---

# 4.1. Pipeline com Airflow

Automatizar o processo que inicialmente era executado manualmente.

### Fluxo

```text
                    AIRFLOW
                       │
                       ↓
               Extração automática
                       │
                       ↓
                 Validação
                       │
                       ↓
                    ETL
                       │
                       ↓
                 PostgreSQL
                       │
                       ↓
                Dados tratados
```

O pipeline deverá ser capaz de:

1. Buscar novos dados;
2. Validar os dados recebidos;
3. Executar o processo de limpeza;
4. Inserir os dados tratados no banco;
5. Registrar a execução;
6. Permitir tratamento de erros e novas tentativas.

---

# 4.2. Evolução da arquitetura

### Versão inicial

```text
Dados
 ↓
Carga manual
 ↓
PostgreSQL
 ↓
ETL
 ↓
Dados tratados
 ↓
Power BI
```

### Versão automatizada

```text
Fonte
 ↓
Airflow
 ↓
Extract
 ↓
Transform
 ↓
Load
 ↓
PostgreSQL
 ↓
Power BI
```

---

# 4.3. Aplicação Streamlit

Criar uma aplicação web para apresentar o projeto de maneira mais amigável e interativa.

Inicialmente, o Streamlit não precisa realizar simulações financeiras complexas.

A primeira versão pode funcionar como uma **interface interativa para exploração dos resultados da análise**.

---

## Possibilidades para o Streamlit

Permitir ao usuário selecionar:

* Ativo;
* Classe de ativo;
* Indicador;
* Período;
* Métrica de comparação.

E apresentar:

```text
Retorno
Volatilidade
Sharpe
Drawdown
Performance histórica
Correlação
```

Além disso, apresentar:

* Explicação dos indicadores;
* Principais insights;
* Gráficos;
* Link para o GitHub;
* Link para o dashboard Power BI;
* Documentação da metodologia.

---

# 4.4. Possível evolução da pergunta inicial

A pergunta inicial:

> **"Baseando-se em dados históricos, onde devo investir R$ 1 milhão?"**

pode ser reformulada durante o projeto caso a análise mostre que ela exige premissas excessivas sobre:

* Tributação;
* Liquidez;
* Prazo;
* Regras de resgate;
* Perfil de risco;
* Custos;
* Reinvestimento.

Uma pergunta mais adequada para a primeira versão seria:

> **"Quais ativos e classes de ativos apresentaram historicamente a melhor relação entre retorno e risco?"**

Outra possibilidade:

> **"Como diferentes ativos e classes de ativos se comportaram historicamente em termos de retorno, risco e consistência?"**

A definição final da pergunta deverá ocorrer após a Etapa 1, quando houver maior compreensão dos dados e indicadores disponíveis.

---

# 📁 Estrutura prevista do projeto

A estrutura poderá evoluir durante o desenvolvimento.

```text
financial-analytics/
│
├── README.md
│
├── docs/
│   ├── project-roadmap.md
│   ├── architecture.md
│   ├── methodology.md
│   └── financial-indicators.md
│
├── data/
│   └── README.md
│
├── sql/
│   ├── schema.sql
│   ├── analysis.sql
│   └── views.sql
│
├── etl/
│   ├── extract.py
│   ├── transform.py
│   └── load.py
│
├── analysis/
│   └── exploratory_analysis.ipynb
│
├── airflow/
│   └── dags/
│
├── powerbi/
│   └── financial_analysis.pbix
│
├── streamlit/
│   └── app.py
│
├── images/
│
└── requirements.txt
```

---

# 🧩 Stack prevista

```text
Python
├── Pandas
├── NumPy
└── bibliotecas de análise/visualização

SQL
└── PostgreSQL

Data Engineering
└── Apache Airflow

Business Intelligence
└── Power BI

Aplicação
└── Streamlit

Versionamento
└── Git / GitHub
```

---

# 🎯 Resultado esperado

Ao final das quatro etapas, o projeto deverá demonstrar a capacidade de:

* Buscar e compreender dados financeiros;
* Trabalhar com dados históricos;
* Realizar limpeza e transformação;
* Utilizar SQL para análise;
* Calcular e interpretar indicadores financeiros;
* Construir análises exploratórias;
* Criar dashboards no Power BI;
* Desenvolver storytelling baseado em dados;
* Automatizar processos com Airflow;
* Trabalhar com PostgreSQL;
* Criar uma aplicação interativa com Streamlit;
* Documentar uma solução de dados de ponta a ponta.

A evolução do projeto será:

```text
                  CONHECIMENTO
                       ↓
                   PLANEJAMENTO
                       ↓
                   IMPLEMENTAÇÃO
                       ↓
                     ANÁLISE
                       ↓
                    DASHBOARD
                       ↓
                   STORYTELLING
                       ↓
                   AUTOMAÇÃO
                       ↓
                   APLICAÇÃO
```

> **Princípio do projeto:** primeiro compreender o problema e os dados, depois construir a solução e, somente após validar a análise, automatizar e disponibilizar o resultado.
