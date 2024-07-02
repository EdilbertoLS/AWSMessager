# AWSMessager
AWSMessager é uma aplicação que usa AWS SNS e SQS para gerenciar mensagens em um ambiente distribuído. SNS publica mensagens para tópicos, enviando-as a múltiplos endpoints, incluindo filas SQS. SQS recebe e armazena mensagens até serem processadas por consumidores, permitindo desacoplamento e escalabilidade
