# Base de Conhecimento

## Dados Utilizados

| Arquivo | Formato | Pra que serve no Eduf |
|---------|---------|---------------------|
| `historico_atendimento.csv` | CSV | Contextualizar interações anteriores, ou seja, dar continuidade ao atendimento de forma mais eficiente. |
| `perfil_investidor.json` | JSON | Personalizar as explicações sobre as dúvidas e necessidades do aprendizado do cliente. |
| `produtos_financeiros.json` | JSON | Conhecer os produtos disponíveis para que eles possam ser ensinados ao cliente. |
| `transacoes.csv` | CSV | Analisar padrão de gastos do cliente e usar essas informações de forma didática. |

---

## Adaptações nos Dados

> Você modificou ou expandiu os dados mockados? Descreva aqui.

O produto Fundo Imobiliário (FII) substituiu o Fundo Multimercado, pois pessoalmente me sinto mais confiante em usar apenas produtos financeiros que conheço. Assim, poderei validar as respostas do Eduf de forma mais acertiva.

---

## Estratégia de Integração

### Como os dados são carregados?
> Existem duas possibilidades, injetar os dados diretamente no prompt (Ctrl + c, Ctrl + v), ou carregar os arquivos via código, como no exemplo abaixo.

```Python
import pandas as pd
import json

# CSVs
historico = pd.read_csv('data/historico_atendimento.csv')
transacoes = pd.read_csv('data/transacoes.csv')

# JSONs
with open('data/perfil_investidor.json', 'r', encoding='utf-8') as f:
    perfil = json.load(f)

with open('data/produtos_financeiros.json', 'r', encoding='utf-8') as f:
    produtos = json.load(f)
```

### Como os dados são usados no prompt?
> Os dados vão no system prompt? São consultados dinamicamente?

```Text
DADOS DO CLIENTE:

PERFIL DO CLIENTE:

TRANSAÇÕES OD CLIENTE:

PRODUTOS DISPONÍVEIS PARA ENSINO:

```

---

## Exemplo de Contexto Montado

> Mostre um exemplo de como os dados são formatados para o agente.

```
Dados do Cliente:
- Nome: João Silva
- Perfil: Moderado
- Saldo disponível: R$ 5.000

Últimas transações:
- 01/11: Supermercado - R$ 450
- 03/11: Streaming - R$ 55
...
```
