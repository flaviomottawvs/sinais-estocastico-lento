# Estratégia de Trading com Estocástico Lento

Este projeto gera sinais de compra e venda baseados em uma estratégia que depende do calculo de diferentes indicadores técnicos (Estocástico Lento, ADX e Média Móvel Exponencial) e itera sobre uma planilha excel com os ativos listados no índice IBOVESPA, para gerar sinais de compra ou venda. A estratégia utiliza  o estocástico lento procurando níveis de sobrecompra e sobrevenda (acima de 80 ou abaixo de 20), a média móvel exponencial de 80 periodos (preço de fechamento do ativo acima da MME80 é considerado tendência de alta, preço de fechamento do ativo abaixo da MME80 é considerado tendência de baixa) e o ADX ( acima de 25 consideramos como uma tendência forte; evitando assim a geração de sinais falsos para ativos lateralizados).

## Recursos Utilizados

- **Python**: Linguagem de programação.
- **Pandas**: Biblioteca para manipulação de dados.
- **NumPy**: Biblioteca para operações matemáticas.
- **pandas_ta**: Biblioteca para cálculo de indicadores técnicos.
- **TvDatafeed**: Biblioteca para integração com a API do TradingView para coleta de dados históricos de preços.
- **Excel**: utilizado em conjunto com o Pandas para se obter a lista de ativos do índice IBOVESPA.


## Estrutura do Projeto

Para que este projeto funcione corretamente, é importante manter uma estrutura específica de diretórios e arquivos. Certifique-se de que seu ambiente de trabalho esteja organizado conforme descrito abaixo:
```
ESTRATEGIA_ESTOCASTICO_LENTO/
│
├── slow_stoch.ipynb # Notebook Jupyter contendo o código principal da estratégia.
└── tickers_ibov.xlsx # Planilha Excel com a lista de tickers a serem analisados.
```



## Configuração do Ambiente

Para configurar seu ambiente de desenvolvimento, siga estas etapas:

1. Clone o repositório:
   ```bash
   git clone https://github.com/flaviomottawvs/sinais-estocastico-lento.git
   cd sinais-estocastico-lento

2. Instale as dependências no seu ambiente de trabalho Python 3: 

   ```bash
   pip install pandas numpy pandas_ta TvDatafeed
   ```
   
Ou Clone a biblioteca TvDatafeed de outro repositório: 

   ```bash
   pip install --upgrade --no-cache-dir git+https://github.com/baselsm/tvdatafeed.git
   ```
   
   
3. Configure suas credenciais do TradingView no seu ambiente:

Para proteger suas credenciais e ao mesmo tempo permitir que o script acesse a API do TradingView, configure as variáveis de ambiente no seu sistema. No Windows, você pode configurar através do Painel de Controle ou diretamente no terminal (o terminal precisa ser reiniciado após a configuração). No macOS e Linux, você pode adicionar estas linhas ao seu arquivo .bashrc, .zshrc, ou similar, dependendo do shell que você usa:

   ```bash
	export TRADINGVIEW_USERNAME='seu_usuario'
	export TRADINGVIEW_PASSWORD='sua_senha'
 ```
 
 
# Estratégia de Trading

## Indicadores Utilizados

MME de 80 períodos: Média móvel exponencial calculada sobre os preços de fechamento.

Inclinação da MME (MME Slope): Calculada como a diferença entre o último valor da MME e o valor de 40 barras antes (Slope Window), dividido pela quantidade de narras usadas para calcular a inclinação dessa MME (Slope Window). A função hiperbólica tangente (tanh) é usada para transformar a inclinação bruta em uma escala que fica entre -1 e 1. Apesar de não validar sinais de compra ou venda, pode ser usado para verificar possíveis mudanças no direcional da média móvel exponencial. 

Estocástico Lento (STOCHd): Média móvel de 3 períodos do %K (estocástico rápido). 

Índice Direcional Médio (ADX): Mede a força da tendência. Um ADX maior que 25 é considerado uma tendência significativamente forte. 

Lógica dos Sinais de Trading

Sinal de Compra: Gerado quando o STOCHd está abaixo de 20 (sobrevendido), o preço está acima da MME80  com ADX maior que 25.

Sinal de Venda: Gerado quando o STOCHd está acima de 80 (sobrecomprado), o preço está abaixo da MME80 com ADX maior que 25.   

## tvDatafeed 

A estratégia pode gerar sinais nos seguintes timeframes suportados pelo tvDatafeed, trocando o valor de interval na função tv.get_hist

Interval.in_1_minute

Interval.in_3_minute

Interval.in_5_minute

Interval.in_15_minute

Interval.in_30_minute

Interval.in_45_minute

Interval.in_1_hour

Interval.in_2_hour

Interval.in_3_hour

Interval.in_4_hour

Interval.in_daily

Interval.in_weekly

Interval.in_monthly

É recomendado que se utilize timeframes mais longos uma vez que a biblioteca tem um atraso de 15 minutos em relação ao mercado parar gerar os dados. 

## Resultados

Os resultados são exibidos em um DataFrame e incluem a data, o preço de fechamento, os valores dos indicadores e o sinal de trading gerado.

## Contribuições

Contribuições para o projeto são bem-vindas. Antes de enviar sua contribuição, por favor, revise as diretrizes de contribuição.

## Licença 

Este projeto está licenciado sob a Licença MIT. Veja o arquivo LICENSE para mais detalhes.

## Contato

Para mais informações, entre em contato com flaviomotta03@gmail.com

