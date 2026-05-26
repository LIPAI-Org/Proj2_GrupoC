# Classificação de Imagens Histológicas

Este repositório contém os códigos, pipelines de experimentação e análises referentes ao **Projeto 2** do Onboarding do LIPAI (Laboratório de Processamento e Análise Interdisciplinar de Imagens). 

O objetivo principal é avaliar modelos de visão computacional modernos para a classificação de imagens histológicas, analisando o impacto de diferentes arquiteturas, estratégias de transferência de aprendizado e técnicas de *Data Augmentation*.

## Integrantes (Grupo C)
* [Gabriel](https://github.com/gabrielhca) - *Engenharia de Modelagem e Pipeline de Treinamento*
* [Guilherme](https://github.com/Guilherme0202PM) - *Análise Estatística e Visualização de Dados*
* [Hanny](https://github.com/hny03) - *Infraestrutura de Dados e Setup Inicial*

## Metodologia Experimental e Reprodutibilidade
O projeto foi estruturado sob um desenho experimental fatorial rigoroso. Para garantir a **reprodutibilidade científica**, todos os testes foram executados com controle estrito de *seeds* matemáticas (42, 123, 2025).

As variáveis do experimento incluem:
* **Arquiteturas:** ConvNeXt V2 (Atto e Pico).
* **Modos de Treinamento:** * *From Scratch* (FS)
  * *Linear Probing / Feature Extraction* (PT-FC)
  * *Fine-Tuning Completo* (PT-ALL)
* **Data Augmentation:** Avaliação comutativa (Com e Sem aplicação).

## Datasets Utilizados
1. **Dataset 1 - Displasia:** Base `OralEpitheliumDB`.
2. **Dataset 2 - NDB:** Base `NDB_UFES`.

## Estrutura do Repositório

* `Displastia.ipynb` e `NDB_UFES.ipynb`: Motores de treinamento automatizados. Contêm as fábricas de modelos, laços de otimização isolados contra vazamento de estado e rotinas de validação.
* `analise_displasia.ipynb` e `analise_NDB.ipynb`: Notebooks dedicados à análise final, extração de métricas (F1-Score Macro/Weighted), curvas de aprendizado e matrizes de confusão.
* `results/`: Diretório gerado dinamicamente que consolida os históricos de perda/acurácia por época em `.json` e o `resultados_consolidados.csv` com as métricas globais e custo computacional (GFLOPs).

## Tecnologias
* **Linguagem:** Python
* **Deep Learning:** PyTorch / Torchvision / Timm
* **Análise e Matemática:** Pandas, NumPy, Scikit-learn
* **Visualização:** Matplotlib, Seaborn
* **Profiling de Modelos:** Thop (Extração de MACs/GFLOPs)
* **Ambiente:** Google Colab (Aceleração em GPU T4)