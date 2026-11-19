# 📚 Sistema de Recomendação Personalizada de Livros

> Projeto desenvolvido no âmbito da disciplina **Projeto Aplicado III** (Faculdade de Computação e Informática — Universidade Presbiteriana Mackenzie.

## 🎯 Problema e Contexto de Negócio

Em livrarias e plataformas literárias com amplos catálogos, o excesso de opções frequentemente gera **indecisão de compra** (*information overload*). Sem referências claras ou curadoria personalizada, o cliente hesita e acaba desistindo da aquisição.

**Nossa Solução:** Um sistema de recomendação baseado em **Aprendizado de Máquina** que analisa o perfil, o histórico de avaliações e as preferências do leitor para sugerir títulos alinhados às suas características — aumentando a conversão de vendas, o engajamento e a descoberta de obras além dos *bestsellers* tradicionais.

---

## 🧠 Arquitetura e Metodologia

O motor de recomendação combina duas abordagens complementares em uma **arquitetura híbrida**

1. **Filtragem Colaborativa (*Collaborative Filtering*):** Utiliza Decomposição em Valores Singulares (**SVD**) para extrair fatores latentes das interações entre usuários e livros, identificando padrões de gosto compartilhados.
2. **Filtragem Baseada em Conteúdo (*Content-Based Filtering*):** Emprega vetorização **TF-IDF** e **Similaridade do Cosseno** sobre os metadados das obras (título, autor, editora e ano) para recomendar títulos similares e mitigar o problema de *cold-start* (itens com poucas avaliações).

### 📊 Resultados Alcançados

| Modelo | RMSE | MAE | Precision@5 | Recall@5 |
| :--- | :---: | :---: | :---: | :---: |
| Baseline — Popularidade Global | 2.1420 | 1.8350 | 0.0420 | 0.0210 |
| Baseline — KNN Item-Based | 1.2850 | 0.9410 | 0.1240 | 0.0890 |
| SVD Refinado (GridSearch) | 0.8740 | 0.6720 | 0.2450 | 0.1980 |
| **Modelo Híbrido (SVD + Conteúdo)** | **0.8410** | **0.6380** | **0.2890** | **0.2310** |

---

## 🛠️ Tecnologias Utilizadas

* **Linguagem:** Python 3.10+[span_6](start_span)[span_6](end_span)
* **Manipulação e Análise de Dados:** `Pandas`, `NumPy`[span_7](start_span)[span_7](end_span)
* **Aprendizado de Máquina e Recomendação:** `Scikit-learn`, `Surprise`[span_8](start_span)[span_8](end_span)
* **Visualização de Dados:** `Matplotlib`, `Seaborn`[span_9](start_span)[span_9](end_span)
* **Base de Dados:** *Book-Crossing Dataset* (`BX-Users`, `BX-Books`, `BX-Book-Ratings`)[span_10](start_span)[span_10](end_span)

---

## 📁 Estrutura do Repositório

```text
├── README.md
├── requirements.txt
├── data/
│   ├── raw/                 # Dados brutos originais
│   └── processed/           # Dados higienizados e filtrados (k-core)
├── notebooks/
│   ├── 01_analise_exploratoria.ipynb
│   ├── 02_prova_de_conceito_baseline.ipynb
│   └── 03_modelo_otimizado_hibrido.ipynb
├── src/
│   ├── data_processing.py   # Pipeline de limpeza e matriz usuário-item
│   ├── models.py            # Implementação dos modelos SVD e Híbrido
│   └── evaluation.py        # Cálculo de RMSE, MAE, Precision@K e Recall@K
└── docs/
    └── relatorio_final.pdf
