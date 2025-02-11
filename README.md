# Análise de Cobertura do Mix Ideal de SKUs

## Descrição do Projeto

Este projeto tem como objetivo analisar a cobertura do mix ideal de SKUs obrigatórios para apoiar os Coordenadores na conquista das metas estabelecidas. O mix ideal é determinado por uma lista de SKUs que devem ser vendidos, organizados por marca e categoria, adaptados às necessidades de cada cliente.

### Objetivos
- Verificar se o mix ideal está sendo cumprido para cada cliente, por marca e categoria.
- Identificar lacunas na cobertura dos SKUs obrigatórios.
- Fornecer insights para que os Coordenadores possam ajustar estratégias de vendas.

## Estrutura dos Dados

O projeto utiliza cinco arquivos CSV principais:
1. **Fato NotaVenda**: Contém informações sobre as vendas, incluindo negócio, data de faturamento, código do produto, código da divisão comercial, código do coordenador, código do cliente, quantidade de caixas vendidas e receita gerada.
2. **Dim Coordenador**: Contém detalhes sobre os coordenadores.
3. **Dim Cliente**: Contém detalhes sobre os clientes.
4. **Dim Divisao Comercial**: Contém detalhes sobre as divisões comerciais.
5. **Dim Produto**: Contém detalhes sobre os produtos.
6. **Dim Empresa**: Contém detalhes sobre as empresas.
7. **Tbl_MixIdeal**: Contém a lista de SKUs obrigatórios por marca e categoria para cada cliente.

## Ferramentas Utilizadas

- **Qlik Sense**: Utilizado para visualização de dados e criação de dashboards interativos.
- **Google Cloud Platform (GCP)**:
  - **Storage Bucket**: Armazenamento dos arquivos CSV brutos e processados.
  - **BigQuery**: Execução de consultas SQL para análise e transformação dos dados.
  - **SQL**: Linguagem utilizada para manipulação e consulta dos dados no BigQuery.
- **Python**: Para scripts de ETL (Extração, Transformação e Carga) e análise de dados.

## Análise

### Metodologia
A análise foi realizada utilizando uma topologia do tipo estrela, onde a tabela `Fato NotaVenda` é o núcleo central, conectada às tabelas de dimensões (`Dim Coordenador`, `Dim Cliente`, `Dim Divisao Comercial`, `Dim Produto`, `Dim Empresa`) e à tabela `Tbl_MixIdeal`.

### Passos do ETL
1. **Extração**:
   - Carregamento dos dados dos arquivos CSV armazenados no **GCP Storage Bucket**.
   - Importação dos dados para o **BigQuery** para processamento.
2. **Transformação**:
   - Junção das tabelas de dimensões com a tabela fato utilizando consultas SQL no **BigQuery**.
   - Cálculo da cobertura do mix ideal para cada cliente, por marca e categoria.
   - Identificação de lacunas na cobertura dos SKUs obrigatórios.
3. **Carga**:
   - Exportação dos dados processados para o **Qlik Sense** para criação de dashboards e visualizações interativas.
   - Geração de relatórios e insights estratégicos.

### Resultados Esperados
- **Cobertura do Mix Ideal**: Percentual de SKUs obrigatórios vendidos para cada cliente.
- **Identificação de Lacunas**: Clientes e coordenadores com cobertura abaixo de 100%.
- **Insights Estratégicos**: Recomendações para ajustes nas estratégias de vendas, considerando variáveis como cliente, região e outros fatores relevantes.

## Instruções para Reprodução

### Pré-requisitos
- **Google Cloud Platform (GCP)**: Conta ativa com acesso ao Storage Bucket e BigQuery.
- **Qlik Sense**: Licença para criação e visualização de dashboards.
- **Python 3.x**: Para execução de scripts de ETL.
- Bibliotecas Python: pandas, google-cloud-storage, google-cloud-bigquery.
