# Classificador de Sentimentos com BERT

## Descrição

Este projeto implementa um classificador de sentimentos utilizando o modelo pré-treinado BERT (Bidirectional Encoder Representations from Transformers) da biblioteca Hugging Face Transformers. O classificador é treinado para classificar avaliações de produtos do site Yelp em sentimentos positivos e negativos, utilizando um conjunto de dados de avaliações.

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
git clone https://github.com/seu-usuario/nome-do-repositorio.git
cd nome-do-repositorio
```

2. Execute o script de treinamento:

```bash
python train.py
```

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

## Contribuições

Contribuições são bem-vindas! Sinta-se à vontade para abrir uma issue ou enviar um pull request.

## Licença

Este projeto está licenciado sob a MIT License. Veja o arquivo [LICENSE](LICENSE) para mais detalhes.

---

## Contato

Se você tiver alguma dúvida ou sugestão, sinta-se à vontade para entrar em contato:

- **Nome**: Winicius B. Faquieri
- **Email**: wfaquieri@gmail.com
- **GitHub**: [swfaquieri](https://github.com/wfaquieri)
