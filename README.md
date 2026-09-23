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

<!-- Preencha com os valores obtidos ao executar o notebook -->

| Modelo | Acurácia | Precisão | Recall | F1 | ROC AUC |
|---|---|---|---|---|---|
| Regressão Logística | | | | | |
| Random Forest | | | | | |

## Principais conclusões

<!-- Escreva com suas palavras o que os resultados mostraram -->

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
