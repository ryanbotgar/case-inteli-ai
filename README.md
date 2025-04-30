# Projeto de Previsão de Churn - TelecomPlus
## Autor: Ryan Gartlan

## Descrição do Projeto
Este projeto desenvolve um modelo de Machine Learning para prever o churn (cancelamento) de clientes para a TelecomPlus, uma empresa fictícia de telecomunicações. O objetivo é identificar clientes com alto risco de cancelar seus serviços nos próximos 3 meses, permitindo que a empresa tome medidas preventivas para retê-los.

## Problema de Negócio
A TelecomPlus está enfrentando uma alta taxa de cancelamento de serviços, o que impacta diretamente suas receitas e lucratividade. Prever quais clientes têm maior probabilidade de cancelar permite direcionar esforços de retenção, oferecendo incentivos e melhorias antes que o cliente decida sair.

## Estrutura do Projeto
O projeto está organizado em 8 arquivos Python, cada um representando uma etapa do processo:

1. **1-Bibliotecas.py**: Importação de todas as bibliotecas necessárias
2. **2-Exploracao.py**: Análise exploratória dos dados para entender padrões e correlações
3. **3-Preprocessamento.py**: Tratamento dos dados e engenharia de features
4. **4-Insights.py**: Formulação de hipóteses sobre os fatores que influenciam o churn
5. **5-Treinamento.py**: Implementação e comparação de três algoritmos de classificação
6. **6-Otimizacao.py**: Ajuste fino dos hiperparâmetros do melhor modelo (versão otimizada)
7. **7-FeatureImportance.py**: Identificação dos principais fatores que influenciam o churn
8. **8-Previsao.py**: Geração de previsões finais e criação do arquivo de resultados
9. **9-Conclusoes.py**: Síntese dos resultados e recomendações para a empresa

## Conjunto de Dados
Foram utilizados dois conjuntos de dados:
- **dados_clientes.csv**: Conjunto de treinamento com ~99.000 registros, contendo informações sobre clientes e indicador de churn
- **desafio.csv**: Conjunto de teste com 5.000 registros, sem a informação de churn, que precisamos prever

Os dados incluem informações como:
- Dados demográficos (idade, gênero, estado civil)
- Informações de contrato (tipo, tempo como cliente, valor mensal)
- Comportamento do cliente (suporte contatado, chamados abertos, reclamações)
- Produtos e serviços assinados

## Metodologia

### Pré-processamento
- Tratamento da coluna 'produtos_assinados', convertendo-a em features binárias para cada produto
- Criação de features derivadas importantes:
  - gasto_medio_mensal = total_gasto / tempo_como_cliente
  - taxa_reclamacoes = reclamacoes / tempo_como_cliente
  - taxa_atrasos = atrasos_pagamento / tempo_como_cliente
- Padronização das variáveis numéricas
- Codificação one-hot das variáveis categóricas

### Modelagem
Implementamos três algoritmos de classificação:
1. **Regressão Logística**: Modelo linear interpretável
2. **Random Forest**: Modelo baseado em árvores com boa capacidade preditiva
3. **Gradient Boosting**: Modelo de ensemble com alta performance

Os modelos foram avaliados com base em múltiplas métricas:
- Acurácia
- Precisão
- Recall
- F1-Score
- AUC-ROC

O melhor modelo foi otimizado para maximizar a performance através da seleção de hiperparâmetros ótimos.

## Principais Insights

1. **Tipo de contrato**: Clientes com contratos mensais têm probabilidade significativamente maior de cancelamento, comparados a clientes com contratos anuais.

2. **Tempo como cliente**: Clientes mais antigos tendem a ser mais fiéis, apresentando menor probabilidade de churn.

3. **Reclamações**: O número de reclamações apresenta forte correlação positiva com a probabilidade de cancelamento.

4. **Valor mensal**: Clientes com valores mensais mais altos têm maior tendência a buscar alternativas.

5. **Produtos e serviços**: Quanto mais serviços e produtos um cliente possui, menor a probabilidade de cancelamento.

## Resultados
O modelo final conseguiu identificar com precisão os clientes com alto risco de churn, atingindo uma acurácia superior a 70% no conjunto de validação.

## Recomendações para a Empresa

1. **Migração para contratos anuais**: Desenvolver campanhas para incentivar clientes com contratos mensais a migrarem para anuais, oferecendo descontos ou benefícios exclusivos.

2. **Programa de fidelidade**: Implementar um programa que recompense clientes antigos, fortalecendo o relacionamento e aumentando os custos de saída.

3. **Melhorar atendimento**: Investir em treinamento da equipe de suporte e processos internos para reduzir o número de reclamações e melhorar a experiência do cliente.

4. **Pacotes de serviços**: Criar pacotes com múltiplos serviços a preços vantajosos, aumentando a integração do cliente com a empresa.

5. **Revisão de preços**: Analisar a precificação para clientes com valores mensais elevados, potencialmente oferecendo descontos para aqueles identificados como de alto risco.

## Como Executar o Projeto

1. Baixe todos os arquivos Python e os conjuntos de dados para a mesma pasta
2. Execute os arquivos na ordem numérica usando o Jupyter Notebook:
   ```
   %run 1-Bibliotecas.py
   %run 2-Exploracao.py
   %run 3-Preprocessamento.py
   %run 4-Insights.py
   %run 5-Treinamento.py
   %run 6-Otimizacao.py
   %run 7-FeatureImportance.py
   %run 8-Previsao.py
   %run 9-Conclusoes.py
   ```

3. O resultado final é salvo no arquivo `resultado_ryan_gartlan.csv`

## Requisitos
- Python 3.7+
- pandas
- numpy
- scikit-learn
- matplotlib
- seaborn
- xgboost
