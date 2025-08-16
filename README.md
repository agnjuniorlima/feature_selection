# Relatório Final da Tarefa Computacional 1: Feature Selection
**Disciplina:** Computação Natural

**Autor:** Agnelo Pereira Lima Júnior

<agnelo.lima@edu.ufes.br>

<agnjuniorlima@gmail.com>

**Data:** 15 de Agosto de 2025

---

### 1. Introdução
Este relatório apresenta a análise dos resultados obtidos na aplicação de Algoritmos Evolutivos (GA e DE) para a seleção de características e otimização de hiperparâmetros de Redes Neurais. Os experimentos foram realizados em três datasets da UCI: Wine e Hepatitis para tarefas de classificação, e Diabetes para uma tarefa de regressão. A eficácia dos modelos foi avaliada e comparada com os resultados do artigo "Improved salp swarm algorithm for feature selection".

### 2. Metodologia Resumida
A abordagem utilizou um algoritmo evolutivo (GA ou DE) para otimizar um indivíduo que codifica tanto um subconjunto de características quanto os hiperparâmetros da rede neural. A função de fitness foi projetada para buscar um equilíbrio entre a minimização do erro (classificação ou regressão) e a redução do número de features, conforme a metodologia do artigo. Para a classificação, foram utilizados os métodos de treino Backpropagation e ELM. Para a regressão, utilizou-se o Backpropagation.

## 3. Ambiente e Parâmetros
## 3.1. Ambiente de Execução
O treinamento e a otimização foram realizados em um ambiente com a seguinte configuração:

Processador (CPU): 12th Gen Intel(R) Core(TM) i7-1265U 1.80 GHz

Memória RAM: 16,0 GB

Sistema Operacional: Sistema operacional de 64 bits, processador baseado em x64

## 3.2. Parâmetros de Treinamento
Os principais parâmetros utilizados nos experimentos foram:

- Algoritmos Evolutivos (GA e DE):

  - Tamanho da População (size_pop): 30 (Classificação) / 30 (Regressão)

  - Número de Gerações (max_iter): 50 (Classificação) / 40 (Regressão)

  - Probabilidade de Mutação (GA): 0.01

- Rede Neural (Otimização):

    - Neurônios por Camada: Otimizado no intervalo [5, 50] para classificação e [5, 100] para regressão.

    - Taxa de Aprendizado: Otimizado no intervalo [0.001, 0.1].

- Função de Fitness:

    - Fator de Ponderação do Erro (rho): 0.9

    - Validação Cruzada (avaliação): 5-fold (Classificação) / 3-fold (Regressão)

### 4. Resultados de Classificação
### 4.1. Dataset: Wine
Análise de Convergência (Backpropagation)
Os algoritmos convergiram para soluções de baixo custo. O DE mostrou-se ligeiramente superior.

<img width="863" height="471" alt="image" src="https://github.com/user-attachments/assets/9d9b83d9-c70b-47b4-b085-7f6873cbd10b" />

<img width="855" height="471" alt="image" src="https://github.com/user-attachments/assets/63ad0801-51bb-4dcc-bee8-2496d1f7db59" />


Eficácia e Comparativo (Backpropagation)
O algoritmo campeão foi o DE (Evolução Diferencial), que obteve uma acurácia de 85% no conjunto de teste.

Métricas no Conjunto de Teste:

              precision    recall  f1-score   support
           0       0.83      0.83      0.83        18
           1       0.84      0.76      0.80        21
           2       0.88      1.00      0.94        15
    accuracy                           0.85        54
   macro avg       0.85      0.87      0.86        54
weighted avg       0.85      0.85      0.85        54
Comparação com o Artigo:
| Métrica | Resultado Obtido (DE + Rede Neural) | Resultado do Artigo (GA + KNN) |
| :--- | :---: | :---: |
| Acurácia | 85.0% | 95.7% |

Resultados com ELM
A abordagem com ELM para o dataset Wine não foi bem-sucedida, apresentando instabilidade e resultando em uma acurácia de apenas 63%.

### 4.2. Dataset: Hepatitis
Análise de Convergência (Backpropagation)
<img width="863" height="471" alt="image" src="https://github.com/user-attachments/assets/45cbc3bc-cf42-4845-9eb9-64e9325a9f31" />


<img width="855" height="471" alt="image" src="https://github.com/user-attachments/assets/cdc04dd6-71aa-4f33-8a67-8c1f33174f87" />


Eficácia e Comparativo (Backpropagation)
O campeão foi o DE (Evolução Diferencial), alcançando 81% de acurácia.

Métricas no Conjunto de Teste:

              precision    recall  f1-score   support
           1       0.50      0.22      0.31         9
           2       0.84      0.95      0.89        38
    accuracy                           0.81        47
   macro avg       0.67      0.58      0.60        47
weighted avg       0.77      0.81      0.78        47
Comparação com o Artigo:
| Métrica | Resultado Obtido (DE + Rede Neural) | Resultado do Artigo (GA + KNN) |
| :--- | :---: | :---: |
| Acurácia | 81.0% | 87.5% |

Resultados com ELM
O ELM também falhou para o dataset Hepatitis, com uma acurácia final de apenas 17%, indicando que o método não é adequado para este problema na configuração testada.

### 5. Resultados de Regressão
### 5.1. Dataset: Diabetes
Análise de Convergência (Backpropagation)
Os algoritmos buscaram minimizar o Erro Quadrático Médio (MSE). O GA encontrou a melhor solução com um fitness final de 2713.89.

<img width="859" height="471" alt="image" src="https://github.com/user-attachments/assets/94238090-924f-42d0-bf6d-227833addbd4" />



<img width="859" height="471" alt="image" src="https://github.com/user-attachments/assets/80e8b09f-4f9e-47a9-8d87-fd8ddaa36460" />


Eficácia (Backpropagation)
O modelo campeão foi treinado e avaliado com métricas de regressão.

Métricas no Conjunto de Teste:

Erro Quadrático Médio (MSE): 2811.06

Coeficiente de Determinação (R²): 0.4793

Comparação com o Artigo:
O artigo de referência foca exclusivamente em problemas de classificação, portanto, não há resultados para o dataset Diabetes que possam ser usados para uma comparação direta. O valor de R² de aproximadamente 0.48 indica que o modelo consegue explicar cerca de 48% da variância nos dados de teste, um resultado moderado que demonstra a viabilidade da abordagem.

### 6. Conclusão Geral
O framework implementado foi bem-sucedido em aplicar Algoritmos Evolutivos para otimização de Redes Neurais em tarefas de classificação e regressão.

Para classificação, a abordagem com Backpropagation mostrou-se robusta, com acurácias de 85% e 81% para os datasets Wine e Hepatitis, respectivamente. O método ELM, por outro lado, foi instável e não produziu resultados úteis.

Para regressão, a metodologia foi adaptada com sucesso para o dataset Diabetes, alcançando um R² de 0.48, o que valida a aplicação da técnica para problemas de previsão de valores contínuos.

Em comparação com o artigo, os resultados de acurácia foram inferiores, o que pode ser atribuído à maior complexidade de otimizar uma Rede Neural em comparação com o classificador KNN utilizado no benchmark.
