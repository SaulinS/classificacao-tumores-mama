# Classificação de Tumores de Mama: Regressão Logística vs Random Forest

Projeto de aprendizado de máquina supervisionado para classificar tumores de mama como malignos ou benignos a partir de medidas extraídas de imagens de exames.

## Objetivo

Comparar a Regressão Logística e o Random Forest Classifier em um problema de classificação binária no qual os tipos de erro têm pesos diferentes: deixar de identificar um tumor maligno (falso negativo) é muito mais grave do que um alarme falso.

## Dataset

**Breast Cancer Wisconsin (Diagnostic)**, disponível no scikit-learn.

- 569 exames, sendo 212 malignos e 357 benignos
- 30 variáveis numéricas calculadas a partir dos núcleos das células (raio, textura, perímetro, área, suavidade, concavidade, entre outras)

## Metodologia

1. Análise exploratória, com atenção ao desbalanceamento das classes
2. Divisão treino/teste estratificada (80/20)
3. Regressão Logística em pipeline com padronização
4. Random Forest Classifier com 200 árvores
5. Avaliação por acurácia, precisão, recall, F1 e ROC AUC, com foco no recall
6. Matriz de confusão e curva ROC
7. Validação cruzada estratificada com 5 folds
8. Comparação entre coeficientes da Regressão Logística e importância das variáveis no Random Forest

## Resultados

Métricas no conjunto de teste (114 exames, sendo 42 malignos). A classe positiva é **maligno**.

| Modelo | Acurácia | Precisão | Recall | F1 | ROC AUC |
|---|---|---|---|---|---|
| **Regressão Logística** | 0,965 | 0,975 | **0,929** | **0,951** | **0,996** |
| Random Forest | 0,965 | **1,000** | 0,905 | 0,950 | 0,994 |

Erros de cada modelo no teste:

| Modelo | Falsos negativos (malignos não detectados) | Falsos positivos (alarmes falsos) |
|---|---|---|
| Regressão Logística | 3 | 1 |
| Random Forest | 4 | 0 |

Validação cruzada estratificada com 5 folds nos dados de treino:

| Modelo | Recall médio | F1 médio |
|---|---|---|
| Regressão Logística | 0,953 ± 0,040 | 0,964 ± 0,021 |
| Random Forest | 0,935 ± 0,039 | 0,949 ± 0,021 |

## Principais conclusões

- **A acurácia sozinha esconderia a diferença entre os modelos.** Os dois acertaram 96,5% dos exames, mas cometeram tipos de erro diferentes.
- **A Regressão Logística é a escolha mais adequada para este problema.** Ela deixou passar 3 tumores malignos, contra 4 do Random Forest. Como um falso negativo é o erro mais grave num diagnóstico, o recall maior pesa mais que a precisão perfeita do Random Forest, que não deu nenhum alarme falso.
- **A vantagem se manteve na validação cruzada,** com recall médio de 95,3% contra 93,5%. Como a diferença é menor que o desvio padrão entre os folds, os dois modelos são próximos, e a escolha se apoia também na simplicidade e na interpretabilidade da Regressão Logística.
- **Os dois modelos separam muito bem as classes** (ROC AUC acima de 0,99). Isso indica que baixar o limiar de decisão, hoje em 0,5, poderia aumentar o recall aceitando alguns alarmes falsos a mais, uma troca razoável neste contexto.
- **Um modelo mais simples pode ser a melhor escolha.** Com variáveis que já separam bem as classes, a Regressão Logística teve desempenho equivalente ou melhor que o Random Forest, com a vantagem de mostrar, pelo sinal de cada coeficiente, se uma medida aumenta ou diminui a chance de o tumor ser maligno.

## Tecnologias

Python · pandas · NumPy · scikit-learn · matplotlib · seaborn

## Como executar

```bash
git clone https://github.com/SaulinS/classificacao-tumores-mama.git
cd classificacao-tumores-mama
pip install -r requirements.txt
jupyter notebook classificacao_tumores.ipynb
```

Também funciona no Google Colab sem instalar nada: basta fazer upload do notebook e executar todas as células. O dataset já vem incluído no scikit-learn.

## Próximos passos

- Ajustar o limiar de decisão para priorizar o recall
- Ajuste de hiperparâmetros com `GridSearchCV`
- Testar SVM e gradient boosting

> Projeto de estudo com dataset público. Não substitui diagnóstico médico.

## Autor

**Saulo Sousa Cunha** · Engenharia de Computação, Universidade SENAI CIMATEC
[LinkedIn](https://linkedin.com/in/saulo-sousa-b2187b256) · [GitHub](https://github.com/SaulinS)
