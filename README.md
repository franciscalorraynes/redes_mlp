# Classificação de Intrusões em Redes com MLP utilizando PyTorch

Este projeto foi desenvolvido como parte da disciplina:

PAM0466 – Sistemas Inteligentes
Semestre: 2026.1

Docente: Pedro Thiago Valério de Souza

---

## Introdução e Contexto

A segurança de redes de computadores é um dos principais desafios da computação moderna, principalmente devido ao crescimento constante de ataques cibernéticos capazes de comprometer serviços, dados e infraestruturas críticas.

Entre os ataques mais comuns estão:

* DoS (Denial of Service)
* Probe
* R2L (Remote to Local)
* U2R (User to Root)

Nesse contexto, Sistemas de Detecção de Intrusão (IDS — Intrusion Detection Systems) são fundamentais para identificar automaticamente atividades maliciosas em redes de computadores.

Como os padrões presentes nos dados de tráfego de rede são altamente não lineares, modelos lineares simples apresentam dificuldades na separação entre conexões normais e conexões maliciosas. Dessa forma, redes neurais MLP tornam-se uma alternativa eficiente para o problema.

---

## Objetivo

O objetivo deste projeto é desenvolver uma rede neural do tipo MLP utilizando PyTorch para classificar conexões da base NSL-KDD em:

* Conexão normal
* Ataque

Buscando auxiliar sistemas de detecção de intrusão em ambientes computacionais.

---

## Dataset

Foi utilizado o dataset NSL-KDD:

http://www.unb.ca/cic/datasets/nsl.html

Arquivos utilizados:

* `KDDTrain+.txt`
* `KDDTest+.txt`

O conjunto de dados possui:

* 41 atributos de entrada
* 3 atributos categóricos:

  * protocol_type
  * service
  * flag
* 38 atributos numéricos
* 1 atributo de saída contendo o tipo de ataque

O problema foi tratado como classificação binária:

* normal → 0
* ataque → 1

---

## Metodologia

O projeto foi desenvolvido nas seguintes etapas:

### 1. Pré-processamento

* Remoção da coluna `difficulty_level`
* Conversão dos atributos categóricos utilizando One-Hot Encoding
* Binarização dos rótulos
* Normalização utilizando `StandardScaler`

### 2. Divisão dos Dados

* 80% treino
* 20% validação

### 3. Modelagem

Foi utilizada uma rede neural MLP implementada em PyTorch.

Arquitetura:

* Camada de entrada
* Primeira camada oculta com 128 neurônios
* Segunda camada oculta com 64 neurônios
* Camada de saída com 1 neurônio

Funções utilizadas:

* ReLU
* BCEWithLogitsLoss
* Adam Optimizer

### 4. Treinamento

* 50 épocas
* Mini-batches de tamanho 256
* DataLoader do PyTorch
* Early Stopping

### 5. Avaliação do Modelo

Foram utilizadas as seguintes métricas:

* Acurácia
* Precisão
* Recall
* F1-score
* Matriz de Confusão

---

## Resultados

O modelo apresentou desempenho satisfatório na tarefa de detecção de intrusões.

Resultados obtidos:

| Métrica  | Valor  |
| -------- | ------ |
| Acurácia | 79,66% |
| Precisão | 92,79% |
| Recall   | 69,69% |
| F1-score | 79,60% |

A elevada precisão indica que o modelo consegue identificar ataques corretamente na maioria das vezes quando realiza uma previsão positiva.

O recall demonstra que ainda existem ataques não detectados, indicando espaço para melhorias futuras no modelo.

---

## Interpretação

Os resultados demonstram que redes neurais MLP possuem boa capacidade de aprendizado para identificação de padrões complexos em tráfego de rede.

Além disso, o projeto evidencia a importância do equilíbrio entre precisão e recall em sistemas de segurança computacional, principalmente devido ao impacto crítico dos falsos negativos em sistemas IDS.

---

## Tecnologias Utilizadas

* Python
* PyTorch
* Pandas
* NumPy
* Matplotlib
* Scikit-learn

---

## Como Executar

Clone o repositório:

```bash
git clone https://github.com/seu-usuario/seu-repositorio.git
```

Instale as dependências:

```bash
pip install torch pandas numpy matplotlib scikit-learn
```

Execute o notebook:

```bash
jupyter notebook
```

Ou execute diretamente no Google Colab.

---

## Autores

* Francisca Lorrayne Santos
* Francisca Samira Aquino França

---

## Considerações Finais

A rede MLP apresentou desempenho adequado para o problema de detecção de intrusão utilizando o dataset NSL-KDD.

O uso de múltiplas camadas ocultas e funções de ativação não lineares permitiu capturar padrões complexos presentes nos dados de tráfego de rede.

Além disso, técnicas como normalização, validação e early stopping contribuíram para melhorar a capacidade de generalização do modelo.

---

## Referências

* NSL-KDD Dataset
  http://www.unb.ca/cic/datasets/nsl.html

* PyTorch Documentation
  https://pytorch.org/docs/stable/index.html

* Scikit-learn Documentation
  https://scikit-learn.org/stable/
