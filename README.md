<div align="center">

# 🐉 Criatura Lendária: Tiamat 🐉

Entrega final da disciplina de Aprendizado de Máquina, ministrada pelo Prof. Dr. Daniel R. Cassar, no curso de Ciência e Tecnologia, Ilum Escola de Ciência (segundo semestre de 2026).

O projeto investiga se o consumo de substâncias psicoativas permite prever o traço de personalidade dominante de uma pessoa, segundo o modelo dos cinco fatores (Big Five). O alvo tem cinco classes: Neuroticismo, Extroversão, Abertura, Amabilidade e Conscienciosidade. Os atributos de entrada são o consumo de 18 substâncias, dois escores de impulsividade e busca de sensações, e atributos demográficos.

Foram comparados cinco pipelines de classificação: regressão logística, k-NN, árvore de decisão, floresta aleatória e gradient boosting. Cada um teve seus hiperparâmetros otimizados com o Optuna, com normalização e redução de dimensionalidade por PCA escolhidas pela própria busca. A avaliação usa o F1 macro, porque as classes são moderadamente desbalanceadas.

</div>

---

## 🛠️ Ferramentas Utilizadas

### Nota sobre o uso de IA

Foram utilizadas as ferramentas de Inteligência Artificial generativa Claude (Anthropic) e Gemini (Google). O Claude auxiliou na escrita de código, na formulação dos gráficos, na depuração de erros e no esclarecimento de dúvidas conceituais. O Gemini foi usado na revisão gramatical e de coesão dos textos. As decisões metodológicas, a escolha das variáveis, a regra de avaliação e a interpretação dos resultados são de autoria própria.

### Bibliotecas e Módulos

- [pandas](https://pandas.pydata.org/)
- [NumPy](https://numpy.org/)
- [scikit-learn](https://scikit-learn.org/)
- [Optuna](https://optuna.org/)
- [SciPy](https://scipy.org/)
- [seaborn](https://seaborn.pydata.org/)
- [Matplotlib](https://matplotlib.org/)

#### Versão do Python

- Python 3.13

---

## 💻 Instalação e Instruções

### Instalação do Código

O código principal é o arquivo `Tiamat.ipynb`. Junto com ele, é necessário o arquivo `drug_consumption.data`, com os dados do Drug Consumption, salvo no mesmo diretório do notebook.

Para executar, use um programa com Jupyter Kernel, como o JupyterLab ou o Visual Studio Code.

### Instalação das Bibliotecas

Antes de executar, instale as bibliotecas listadas acima. Por exemplo, para instalar o Optuna, execute `pip install optuna` em uma célula do notebook.

### Como Usar

1. Abra o `Tiamat.ipynb` e execute as células em ordem, preferencialmente com "Restart Kernel and Run All".
2. O notebook realiza, em sequência: carregamento e tratamento dos dados, remoção de atributos e de duplicatas, divisão treino/teste, checagem de saúde do split, análise exploratória e de associação usando apenas o conjunto de treino, indução e otimização dos cinco pipelines, comparação com cinco sementes de validação e avaliação final no conjunto de teste.
3. Ao final, são exibidos os gráficos de comparação entre os modelos, a matriz de confusão do modelo escolhido e a importância por permutação dos atributos.

---

## 📂 Sobre o Dataset

O dataset é o *Drug Consumption*, disponibilizado no UCI Machine Learning Repository por Fehrman et al. Contém 1885 pessoas com respostas ao questionário de personalidade NEO-FFI-R, ao questionário sociodemográfico e ao consumo declarado de 18 substâncias, além de uma substância de controle (Semeron). O alvo deste trabalho é o traço de personalidade dominante, obtido a partir dos cinco escores do questionário.

## 📊 Principais Resultados

- A linha de base, que sempre prevê a classe mais frequente, obteve F1 macro de 0,083.
- A regressão logística foi escolhida pela regra definida antes do teste: maior média de F1 macro em cinco sementes de validação (0,324 ± 0,005). A floresta aleatória ficou em segundo, com 0,315 ± 0,007.
- No conjunto de teste, o modelo escolhido obteve F1 macro de 0,326, próximo do valor de validação.
- Os atributos com maior importância por permutação foram Impulsivo, Ecstasy, SS e Benzodiazepínicos.

## ⚠️ Limitações do Modelo

- O modelo explica apenas uma parte pequena da informação sobre o traço dominante. O F1 macro de 0,326 supera a linha de base, mas o erro ainda é grande, e a curva de aprendizado sugere que mais exemplos trariam ganhos pequenos.
- Os dados são de autorrelato, coletados por questionário online, e a amostra não é representativa da população: a maioria dos participantes é do Reino Unido e de etnia branca.
- Os hiperparâmetros foram otimizados em uma única divisão treino/validação. A checagem com cinco sementes reduz esse efeito, mas não o elimina.
- Alguns intervalos de busca ficaram perto do limite (profundidade da floresta e valor de C da regressão logística). Isso está registrado no notebook.
- A regra de agrupamento de categorias por contagem foi aplicada à etnia, mas não ao país, o que é uma inconsistência do método.

<div align="center">

# 👤 Desenvolvedor do Projeto 👤

[<img src="https://github.com/PangioAAA.png" width="200"><br><sub>✨Giovanni de Almeida Moreira✨</sub>](https://github.com/PangioAAA)

**Giovanni A. Moreira** (2610060)

Aluno do curso de Ciência e Tecnologia, Ilum Escola de Ciência

</div>

- Desenvolveu o pipeline de tratamento de dados, a análise exploratória e a modelagem com otimização de hiperparâmetros
- Compararam-se cinco pipelines de classificação, avaliados com validação cruzada estratificada e um conjunto de teste reservado
- Interpretou os resultados à luz das limitações dos dados e dos modelos

<div align="center">

Agradecimento especial ao professor da disciplina de Aprendizado de Máquina, por todo o aprendizado:

⭐ Professor Daniel Roberto Cassar

</div>

# 📚 Referências 📚

\[1] FEHRMAN, E.; MUHAMMAD, A. K.; MIRKES, E. M.; EGAN, V.; GORBAN, A. N. The Five Factor Model of Personality and Evaluation of Drug Consumption Risk. Cham: Springer, 2017. (Studies in Classification, Data Analysis, and Knowledge Organization).

\[2] COSTA, P. T.; McCRAE, R. R. Revised NEO Personality Inventory (NEO-PI-R) and NEO Five-Factor Inventory (NEO-FFI) Professional Manual. Odessa, FL: Psychological Assessment Resources, 1992.

\[3] FEHRMAN, E.; EGAN, V.; GORBAN, A. N.; LEVESLEY, J.; MIRKES, E. M.; MUHAMMAD, A. K. Drug Consumption (Quantified). UCI Machine Learning Repository, 2015. Disponível em: https://archive.ics.uci.edu/dataset/373/drug+consumption+quantified. Acesso em: 14 nov. 2026.

\[4] CASSAR, Daniel Roberto. ATP-203: Aprendizado de Máquina: Outras métricas e tipos de classificação. Notebook de aula, Ilum, Escola de Ciência, CNPEM, Campinas, 2026.

\[5] McKINNEY, W. Data Structures for Statistical Computing in Python. In: Proceedings of the 9th Python in Science Conference, p. 56–61, 2010. Documentação do pandas disponível em: https://pandas.pydata.org/docs/. Acesso em: 20 nov. 2026.

\[6] PEDREGOSA, F. et al. Scikit-learn: Machine Learning in Python. Journal of Machine Learning Research, v. 12, p. 2825–2830, 2011. Documentação disponível em: https://scikit-learn.org/stable/. Acesso em: 20 nov. 2026.

\[7] VIRTANEN, P. et al. SciPy 1.0: Fundamental Algorithms for Scientific Computing in Python. Nature Methods, v. 17, p. 261–272, 2020. Documentação disponível em: https://docs.scipy.org/doc/scipy/. Acesso em: 20 nov. 2026.

\[8] CASSAR, Daniel Roberto. ATP-203: Aprendizado de Máquina: Seleção de atributos. Notebook de aula, Ilum, Escola de Ciência, CNPEM, Campinas, 2026.

\[9] CASSAR, Daniel Roberto. ATP-203: Aprendizado de Máquina: Redução de dimensionalidade com PCA. Notebook de aula, Ilum, Escola de Ciência, CNPEM, Campinas, 2026.

\[10] AKIBA, T.; SANO, S.; YANASE, T.; OHTA, T.; KOYAMA, M. Optuna: A Next-generation Hyperparameter Optimization Framework. In: Proceedings of the 25th ACM SIGKDD International Conference on Knowledge Discovery & Data Mining, p. 2623–2631, 2019. Documentação disponível em: https://optuna.readthedocs.io/. Acesso em: 20 nov. 2026.

\[11] CASSAR, Daniel Roberto. LMA-203 8.0: Introdução aos testes de hipótese. Notebook de aula, disciplina de Probabilidade e Estatística, Ilum, Escola de Ciência, 2026. Disponibilizado pelo docente.
