# Previsão-de-Estoque-Inteligente-na-AWS-com-SageMaker-Canvas-DIO

📊 Projeto de Machine Learning com AWS SageMaker Canvas
Predição e Análise de Preços e Estoque de Produtos
Este projeto apresenta a construção de um pipeline de Machine Learning utilizando o AWS SageMaker Canvas, uma ferramenta no-code/low-code da AWS para criação, análise e implantação de modelos de ML sem necessidade de programação.
Utilizei como base um dataset contendo informações de produtos e suas características de preço, promoção e estoque.

📁 Descrição do Dataset
O dataset utilizado contém 1000 registros e as seguintes colunas:
Coluna 				Descrição
ID_PRODUTO			Identificador único de cada produto
DATA_EVENTO			Data de referência do preço e estoque
PRECO				Preço unitário do produto na data analisada
FLAG_PROMOCAO		Indica se o produto estava em promoção (1 = sim, 0 = não)
QUANTIDADE_ESTOQUE	Quantidade de itens disponíveis em estoque
O objetivo do projeto foi explorar, preparar, treinar e avaliar modelos de ML capazes de prever variáveis relacionadas ao comportamento dos produtos — como preço ou estoque — considerando padrões históricos.

🧰 Etapas realizadas no SageMaker Canvas
1️⃣ Upload e preparação dos dados
Importe o arquivo CSV diretamente na interface do SageMaker Canvas.
O Canvas realiza automaticamente detecção de schema, tipos de dados e valores faltantes.
Converti a coluna DATA_EVENTO para o tipo date dentro da ferramenta.
Verifiquei distribuição das variáveis e identifiquei:
Preço variando entre diferentes produtos.
Produtos com ou sem promoção (FLAG_PROMOCAO).
Estoque fixo em 100 itens, com pequenas alterações em datas diferentes.

##2️⃣ Análise exploratória automática (EDA)
O SageMaker Canvas gerou automaticamente:
✔ Gráficos de correlação
✔ Histogramas de distribuição
✔ Insights sobre importância das variáveis
✔ Análise temporal da coluna DATA_EVENTO
Principais observações:
Produtos em promoção geralmente apresentam preços mais baixos.
O ID_PRODUTO funciona como identificador e não como variável preditiva relevante.
PRECO é a variável mais influenciada por promoções e por padrão específico de cada produto.

3️⃣ Definição do objetivo do modelo
Utilizei o Canvas para criar diferentes tipos de previsão:

🔮 Modelos testados
Regressão para prever o preço do produto (PRECO)
Classificação para prever se o produto estará em promoção (FLAG_PROMOCAO)
Regressão para prever quantidade de estoque futura (QUANTIDADE_ESTOQUE)
O modelo final escolhido foi baseado na previsão mais relevante para o negócio (informar no seu caso: preço, estoque ou promoção).

4️⃣ Treinamento automático
O SageMaker Canvas permitiu treinar modelos com apenas alguns cliques:
Seleção do tipo de previsão (“Predict numeric value” ou “Predict category”)
Ajuste automático de hyperparameters
Criação de pipelines offload para o SageMaker Studio, quando necessário
Monitoramento de métricas como: RMSE, MAE, R², Acurácia (no caso de classificação)

5️⃣ Avaliação dos modelos
Após o treinamento, foram gerados:
✔ Feature importance
✔ Matriz de confusão (se classificação)
✔ Gráficos de erro (regressão)
✔ Comparação entre modelos automáticos e modelos rápidos

Exemplos de insights obtidos:
A variável FLAG_PROMOCAO tem forte impacto no PRECO.
Datas mais recentes apresentam padrões mais uniformes no preço.
O estoque não sofre grandes flutuações, mas pode ser estimado com boa precisão.

6️⃣ Geração de previsões
Utilizando a aba "Predict", gerei predições:
Upload de um novo CSV
Previsões individuais ou em lote
Explicabilidade local por SHAP para cada registro
Exportação das previsões em novo arquivo CSV

7️⃣ Exportação e Integração
O SageMaker Canvas permitiu:
Exportar o modelo para uso no SageMaker Studio (Jupyter Notebooks)
Baixar o arquivo com previsões
Integrar previsões com aplicações externas usando API endpoints (se habilitado pelo Studio)

✔️ Resultados do Projeto
Construção completa de um pipeline de Machine Learning sem escrever código.
Entendimento claro das relações entre promoção, preço e estoque.
Criação de um modelo capaz de prever comportamentos futuros dos produtos.
Documentação padronizada para reprodutibilidade do experimento.

🏁 Conclusão
Este projeto demonstra como o AWS SageMaker Canvas permite fluxos rápidos e eficientes de Machine Learning em ambiente corporativo ou acadêmico, possibilitando experimentação e insights de forma visual e acessível. O uso deste dataset permitiu compreender padrões comerciais e testar diferentes abordagens de previsão usando ferramentas avançadas da AWS.
