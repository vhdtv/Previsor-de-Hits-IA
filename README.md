# Previsor de Hits (Spotify) — Comitê de Classificadores

Projeto da UC **Inteligência Artificial** com objetivo de prever se uma música tem potencial para ser **hit** no Spotify, aplicando um **comitê de classificadores** e comparando o desempenho de diferentes algoritmos de IA.

## 🎯 Objetivo
Construir e avaliar modelos de Machine Learning para identificar **hit_potencial** com base em atributos de faixas do Spotify (ex.: energy, danceability, loudness, valence, speechiness, instrumentalness, etc.).

## 🗂️ Estrutura do Repositório
```
/data
    Pasta1.xlsx                   # base de dados (Spotify)
/notebooks
    modelo_arvore.ipynb           # Árvore de Decisão
    modelo_regressao.ipynb        # Regressão (Linear/Logística)
    modelo_knn.ipynb              # KNN
    modelo_kmeans.ipynb           # k-Means
    modelo_naivebayes.ipynb       # Naive Bayes
    integracao_final.ipynb        # consolidação de métricas e gráficos
/docs
    relatorio_final.pdf           # versão final do relatório
    apresentacao_final.pptx       # slides de apresentação
README.md
requirements.txt
```

## 🧩 Definição da Variável Target
- **`hit_potencial`**: definir regra binária a partir de `track_popularity`.
  - Exemplo: `hit_potencial = 1` se `track_popularity >= 80`, caso contrário `0`.
  - A regra pode ser ajustada e **deve ser documentada**.

## 🔧 Preparação dos Dados
1. Carregar `/data/high_popularity_spotify_data.xlsx`.
2. Selecionar variáveis relevantes e tratar **valores nulos**.
3. Codificar variáveis categóricas (ex.: `playlist_genre`, `key`, `mode`) quando necessário.
4. Padronizar/normalizar variáveis para KNN e Regressão/Naive Bayes quando aplicável.
5. Dividir em **treino/teste** (ex.: 80/20) com `train_test_split(random_state=42)`.

## 🧪 Modelos
Cada notebook deve:
- Implementar o algoritmo designado.
- Registrar hiperparâmetros e justificativas.
- Gerar **métricas**: Acurácia, Precisão, Recall, F1; e, se pertinente, **ROC-AUC**.
- Salvar gráficos (matriz de confusão, curvas ROC, distribuição) em `/docs`.
- Exportar um **dic**/`json` de resultados para integração (ex.: `results/modelo_arvore.json`).

### Algoritmos
- **Árvore de Decisão** (`DecisionTreeClassifier`)
- **Regressão Logística** (`LogisticRegression`) e/ou **Regressão Linear** (se o target for contínuo)
- **KNN** (`KNeighborsClassifier`)
- **k-Means** (`KMeans`) para análise não supervisionada (opcionalmente rotular por proximidade)
- **Naive Bayes** (`GaussianNB`/`MultinomialNB` conforme features)

## 📊 Integração
O notebook `integracao_final.ipynb` deve:
- Carregar os `json` de métricas de cada modelo.
- Construir uma **tabela comparativa** com todas as métricas.
- Gerar gráficos comparativos (ex.: barras por F1/ROC-AUC).
- Indicar **modelo vencedor** por critério acordado (ex.: maior F1/ROC-AUC). 

## 📝 Relatório e Apresentação
**Relatório (PDF)**
1. Introdução e objetivo.
2. Base de dados e variáveis.
3. Metodologia e preparação.
4. Resultados por algoritmo.
5. Comparação e discussão.
6. Conclusões e trabalhos futuros.

**Apresentação (PPT)**
- Contexto, dados, modelos, resultados (gráficos), conclusão e próximos passos.

## 🧭 Fluxo de Trabalho (Git)
- Branch por modelo: `feat/modelo-arvore`, `feat/modelo-regressao`, etc.
- Pull Requests revisados antes de merge em `main`.
- Commits descritivos: `feat(tree): treino e métricas iniciais`.

## 🚀 Execução Rápida
```bash
# (opcional) criar venv
python -m venv .venv
source .venv/bin/activate  # Windows: .venv\Scripts\activate

# instalar dependências
pip install -r requirements.txt

# iniciar Jupyter
jupyter lab  # ou jupyter notebook
```

## ✅ Qualidade e Reprodutibilidade
- Fixar `random_state=42` onde aplicável.
- Documentar toda transformação de dados.
- Salvar versões dos arquivos e métricas.

## ⚠️ Observações
- Verificar licenças e termos do dataset original (Kaggle).
- Evitar commitar dados sensíveis.

## 📅 Deadline
- **Entrega final**: 21/11/2025

---

Caso precise, disponibilizamos **scripts utilitários** para padronizar carregamento, split e avaliação em `/utils`.
