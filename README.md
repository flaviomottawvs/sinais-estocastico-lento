# Estratégia de Trading com Estocástico Lento

Este projeto implementa uma estratégia de trading automático baseada na análise técnica de ações listadas na BM&FBOVESPA. A estratégia utiliza indicadores como o estocástico lento, a inclinação da média móvel exponencial (MME) e o índice direcional médio (ADX) para gerar sinais de compra e venda.

## Recursos Utilizados

- **Python**: Linguagem de programação.
- **Pandas**: Biblioteca para manipulação de dados.
- **NumPy**: Biblioteca para operações matemáticas.
- **pandas_ta**: Biblioteca para cálculo de indicadores técnicos.
- **tvDatafeed**: Biblioteca para integração com a API do TradingView para coleta de dados históricos de preços.

## Configuração do Ambiente

Para configurar seu ambiente de desenvolvimento, siga estas etapas:

1. Clone o repositório:
   ```bash
   git clone https://github.com/flaviomottawvs/sinais-estocastico-lento.git
   cd sinais-estocastico-lento

2. Instale as dependências: 

   ```bash
   pip install pandas numpy pandas_ta tvDatafeed
   
   
3. Configure suas credenciais do TradingView no seu ambiente:

Para proteger suas credenciais e ao mesmo tempo permitir que o script acesse a API do TradingView, configure as variáveis de ambiente no seu sistema. No Windows, você pode configurar através do Painel de Controle ou diretamente no terminal (o terminal precisa ser reiniciado após a configuração). No macOS e Linux, você pode adicionar estas linhas ao seu arquivo .bashrc, .zshrc, ou similar, dependendo do shell que você usa:

   ```bash
	export TRADINGVIEW_USERNAME='seu_usuario'
	export TRADINGVIEW_PASSWORD='sua_senha'
 ```
# Estratégia de Trading

## Indicadores Utilizados

MME de 80 períodos: Média móvel exponencial calculada sobre os preços de fechamento.

Inclinação da MME: Calculada como a diferença entre o último valor da MME e o valor de 40 barras antes, dividido por 40. A função hiperbólica tangente (tanh) é usada para transformar a inclinação bruta em uma escala que fica entre -1 e 1.

Estocástico Lento (STOCHd): Média móvel de 3 períodos do %K (estocástico rápido).

Índice Direcional Médio (ADX): Mede a força da tendência.

Lógica dos Sinais de Trading

Sinal de Compra: Gerado quando o STOCHd está abaixo de 20 (sobrevendido), o preço está acima da MME80 e a MME80 está inclinada para cima com ADX maior que 25.

Sinal de Venda: Gerado quando o STOCHd está acima de 80 (sobrecomprado), o preço está abaixo da MME80 e a MME80 está inclinada para baixo com ADX maior que 25.   


## Resultados

Os resultados são exibidos em um DataFrame e incluem a data, o preço de fechamento, os valores dos indicadores e o sinal de trading gerado.

## Contribuições

Contribuições para o projeto são bem-vindas. Antes de enviar sua contribuição, por favor, revise as diretrizes de contribuição.

## Licença 

Este projeto está licenciado sob a Licença MIT. Veja o arquivo LICENSE para mais detalhes.

## Contato

Para mais informações, entre em contato com flaviomotta03@gmail.com

