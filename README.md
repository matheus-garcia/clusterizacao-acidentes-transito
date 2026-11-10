# Análise de Agrupamentos: Acidentes de Trânsito nas Capitais Brasileiras

Projeto de conclusão da **Especialização em Engenharia de Software para Aplicações de Ciência de Dados (UFRGS, 2026)**.
Orientador: Prof. Dr. Leandro Krug Wilves.

## Problema

Acidentes de trânsito são um dos principais problemas de saúde pública e mobilidade urbana no Brasil. O objetivo deste trabalho foi identificar **perfis de acidentes** nas capitais brasileiras, combinando variáveis numéricas e categóricas, para apoiar políticas públicas de segurança viária mais direcionadas.

## Dados

- **Fonte:** Registro Nacional de Acidentes e Estatísticas de Trânsito (RENAEST), portal de dados abertos do Ministério dos Transportes.
- **Período:** 2019 a 2024.
- **Bases integradas:** acidentes, vítimas, tipo de veículo e localidades.
- **Dataset final:** cerca de **1,88 milhão de registros e 61 colunas**.

Os arquivos de dados não estão no repositório por causa do tamanho; o notebook de preparação baixa a base diretamente do portal.

## Método

1. **Ingestão:** download e extração automatizados da base pública (`wget` / `unzip` no Google Colab).
2. **Preparação (`data_wrangling_tcc.ipynb`):** filtragem para as capitais e para o período 2019–2024, análise de valores ausentes, padronização de categorias inconsistentes, normalização de textos e integração das quatro bases.
3. **Modelagem (`clustering_tcc_ufrgs.ipynb`):**
   - algoritmo **k-prototypes** (biblioteca `kmodes`), adequado a dados mistos;
   - padronização das variáveis numéricas (`StandardScaler`);
   - prototipagem em amostra de 15 mil registros e execução na base completa;
   - teste de 2 a 10 grupos, avaliados por custo, **Davies-Bouldin** e **Calinski-Harabasz**;
   - tratamento de variáveis de alta cardinalidade para viabilizar o processamento em memória.

## Resultados

A solução com **6 clusters** apresentou o melhor equilíbrio entre coesão interna e separação entre grupos. Os perfis se diferenciam por tipo de veículo, gravidade, distribuição temporal, suspeita de consumo de álcool e impacto sobre as vítimas, com distribuição bastante heterogênea entre regiões e capitais, o que indica forte influência de fatores locais.

## Tecnologias

Python · pandas · NumPy · scikit-learn · kmodes · Matplotlib · Seaborn · Google Colab

## Como executar

1. Abra os notebooks no Google Colab (ou em um ambiente Jupyter com Python 3).
2. Execute primeiro `data_wrangling_tcc.ipynb` para baixar e preparar os dados.
3. Em seguida, execute `clustering_tcc_ufrgs.ipynb` com o arquivo `df_final.csv` gerado.

## Autor

**Matheus dos Santos Garcia** – Analista de Dados
[LinkedIn](https://www.linkedin.com/in/matheussgarcia/)
