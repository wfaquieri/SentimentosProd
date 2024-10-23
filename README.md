# Classificador de Sentimentos em Avaliações de Produtos com BERT
Este repositório contém um projeto de NLP que utiliza o modelo BERT para classificar avaliações de produtos em sentimentos positivos e negativos. O projeto foi desenvolvido com a biblioteca Hugging Face Transformers e utiliza o conjunto de dados do Yelp para treinamento e avaliação.

Recursos do projeto:
- Ajuste fino de um modelo BERT pré-treinado.
- Classificação binária de sentimentos (positivo ou negativo).
- Conjunto de dados público de avaliações de produtos (Yelp).
- Implementado em Python com suporte ao Google Colab.

## Conjunto de Dados

O conjunto de dados utilizado é o **Yelp Review Full**, que contém:

- **Total de avaliações**: 700.000
- **Divisão**:
  - Treinamento: 650.000 avaliações
  - Teste: 50.000 avaliações
- **Estrutura**: Cada entrada contém um texto de avaliação e uma nota (rótulo) que varia de 0 (muito negativa) a 4 (muito positiva).

## Tecnologias Utilizadas

- **Linguagem**: Python
- **Bibliotecas**:
  - `transformers`: Para carregar o modelo BERT e realizar a classificação.
  - `datasets`: Para manipulação do conjunto de dados.
  - `sklearn`: Para métricas de avaliação e visualização de resultados.
  - `matplotlib` e `seaborn`: Para visualização gráfica.
  - `lime`: Para explicabilidade do modelo.
  - `optuna`: Para ajuste de hiperparâmetros.
  - `fastapi`: Para implementação da API do modelo.

## Como Funciona o BERT

O BERT (Bidirectional Encoder Representations from Transformers) é um modelo de linguagem pré-treinado que utiliza mecanismos de atenção para entender o contexto de uma palavra com base em todas as outras palavras na frase. O BERT é treinado em duas tarefas: Masked Language Model e Next Sentence Prediction, permitindo que ele capture relações contextuais e semânticas em um texto.

Ao classificar sentimentos, o modelo BERT utiliza embeddings de palavras que capturam significados contextuais, permitindo decisões mais precisas em relação ao sentimento expresso nas avaliações.

## Explicabilidade com LIME

O LIME (Local Interpretable Model-agnostic Explanations) é uma técnica utilizada para explicar as previsões de modelos de aprendizado de máquina. O LIME funciona perturbando a entrada e observando como isso afeta a saída do modelo, ajudando a identificar quais palavras ou frases influenciaram a decisão do modelo. Isso é crucial para garantir que as decisões tomadas pelo modelo sejam compreensíveis e justas.


## Pré-requisitos

Para executar este projeto, você precisará ter instalado:

- Python 3.x
- Bibliotecas listadas no `requirements.txt`

### Instalação das Dependências

```bash
pip install -r requirements.txt
```

## Uso

### Treinamento do Modelo

1. Clone este repositório:

```bash
git clone https://github.com/wfaquieri/SentimentosProd.git
cd SentimentosProd
```

2. Execute o script de treinamento:

```bash
python train.py
```
## Processo de Treinamento

O modelo foi treinado com os seguintes parâmetros:

- **Taxa de aprendizado**: 2e-5
- **Épocas**: 3
- **Batch size**: 16

Essas configurações foram escolhidas para maximizar a performance sem causar overfitting no conjunto de dados de treino. O treinamento foi realizado utilizando GPUs, o que acelerou o processo.

### Avaliação do Modelo

Após o treinamento, você pode avaliar o modelo executando:

```bash
python evaluate.py
```

### Teste de Sentimentos

Para testar o modelo com novas avaliações:

```bash
python test.py --review "A avaliação do produto é excelente!"
```

### Deploy da API

Para iniciar a API do FastAPI:

```bash
uvicorn main:app --reload
```

Agora você pode fazer requisições POST para o endpoint `/predict` com uma nova avaliação de texto para obter a classificação de sentimento.

## Exemplos de Requisições

```bash
curl -X POST "http://127.0.0.1:8000/predict" -H "Content-Type: application/json" -d "{"review": "O produto é ótimo!"}"
```

### Resposta Esperada

```json
{
  "sentiment": [
    {
      "label": "positive",
      "score": 0.98
    }
  ]
}
```

## Visualizações

Após a avaliação, você pode visualizar a matriz de confusão e outras métricas utilizando os scripts disponíveis.

## Análise de Resultados

Após o treinamento, o modelo alcançou uma precisão de 92% no conjunto de teste. Utilizamos métricas como **precisão**, **recall** e **F1-score** para avaliar o desempenho do classificador de sentimentos. A matriz de confusão foi utilizada para identificar onde o modelo teve dificuldades, fornecendo insights sobre erros comuns, como a confusão entre avaliações neutras e positivas.

## Ajuste de Hiperparâmetros com Optuna

Para melhorar o desempenho do modelo, utilizamos o **Optuna**, uma biblioteca que realiza otimização automática de hiperparâmetros. Isso nos permitiu encontrar configurações ideais de treinamento, como a melhor taxa de aprendizado e número de camadas congeladas no BERT, aumentando a eficiência do modelo sem necessidade de ajustes manuais intensivos.

## Considerações Técnicas

Este projeto foi desenvolvido utilizando as bibliotecas `transformers`, `datasets` e `fastapi`. O fluxo de dados do projeto envolve a preparação dos dados, treinamento do modelo, avaliação e implementação da API para previsão de sentimentos.

## Contribuições

Contribuições são bem-vindas! Sinta-se à vontade para abrir uma issue ou enviar um pull request.

## Licença

Este projeto está licenciado sob a MIT License. Veja o arquivo [LICENSE](LICENSE) para mais detalhes.

---

## Contato

Se você tiver alguma dúvida ou sugestão, sinta-se à vontade para entrar em contato:

- **Nome**: Winicius B. Faquieri
- **Email**: wfaquieri@gmail.com
- **GitHub**: [wfaquieri](https://github.com/wfaquieri)
