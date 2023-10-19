# projeto_pipeline_de_dados_telegram

O **projeto** consiste na criação de uma pipeline completa de dados utilizando a AWS para um chatbot no aplicativo Telegram, que permite aos usuários interagirem enviando mensagens para o bot. Essas mensagens são captadas em tempo real através da API de bots do Telegram e redirecionadas por meio de um Webhook do AWS API Gateway.

As mensagens redirecionadas passam por uma etapa de processamento simplificada, usando uma função do AWS Lambda. Os dados resultantes são armazenados no formato ".json" na primeira camada de um Data Lake (AWS S3).

Diariamente, em um horário fixo pré determinado, um processo automatizado é acionado pelo AWS Event Bridge. Esse processo consiste em um ETL (Extração, Transformação e Carga), extraindo todos os dados "crus" do dia anterior na primeira camada do Data Lake. Os dados são então processados e enriquecidos por meio de outra função do AWS Lambda e são armazenados na segunda camada do Data Lake. Nessa segunda camada, os dados são armazenados no formato .parquet.

Foi então criada uma tabela no AWS Athena, permitindo acesso rápido e simplificado dos dados já processados, prontos para serem analisados e transformados em insights.
