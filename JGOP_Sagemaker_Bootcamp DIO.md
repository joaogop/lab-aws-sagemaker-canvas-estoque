# 1. Seleção de Datasets

  Dataset escolhido foi o "dataset-1000-com-preco-promocional-e-renovacao-estoque.csv", disponibilizado pela DIO.

# 2. Construção do Modelo

  Parâmetros:
    - Considerar feriados brasileiros
    - Tipo de Modelo: Time Series Forecasting (usado por ser sugerido para responder perguntas de como manter o estoque antes de uma feriado)
    - Dias a serem previstos: 4
    - Coluna Target: QUANTIDADE_ESTOQUE
    - Coluna de ID: ID_PRODUTO
    - Substituir vazios na coluna PRECOS pela MEDIANA (cogitado usar a média, mas foi sugerido a mediana)
    - Substituir vazios na coluna QUANTIDADE_ESTOQUE por 0 (zero)
    - Modelo treinado em Quick Build, então espera-se que ele apresente uma qualidade inferior

# 3. Análise do Modelo:

  Resultados do modelo:
  
![image](https://github.com/user-attachments/assets/1a56373f-ed00-4a97-8de7-0ae40d77c494)

  Considerando a tabela abaixo, nota-se que o MAPE indica que esse modelo é altamente acurado, dado que ele está abaixo de 10% (1,2%).
  ![image](https://github.com/user-attachments/assets/a095a59c-7c61-4bb4-9de1-9a34dcbd9cdf)

  Por outro lado, o MASE já apresenta um resultado menos impressionante. Com o valor próximo de 1 indica que o modelo de previsão tem um desempenho semelhante a um ponto de referência ingênuo. Embora isso sugira que o modelo não está se saindo mal, também implica que pode haver oportunidades de melhoria.

  Além disso, a coluna que apresenta o maior impacto para a previsão foi o preço.
  ![image](https://github.com/user-attachments/assets/0f654584-7890-4a19-bb32-d66a99ad044a)


# 4. Previsão

  Apóes treinado, o modelo foi usado para prever o estoque daqui 4 dias.

  Extraindo o resultado de alguns produtos:
    Legenda:
      ![image](https://github.com/user-attachments/assets/507b9cff-0934-4620-a970-8a462a9bf059)
      
  ID 1008:
    ![1008](https://github.com/user-attachments/assets/46cb89a3-393d-41c9-8ee3-ee85bffc27ef)

  ID 1018:
    ![1018](https://github.com/user-attachments/assets/07517597-08d9-4bb0-9036-9da06ab208bb)

  ID 1022:
    ![1022](https://github.com/user-attachments/assets/a29f6a74-b2a7-47f6-a1e1-659ce3ef4695)


  Considerando esses 3 exemplos, nota-se que os produtos podem se comportar de forma extremamente diferente um do outro.
  No caso do 1008 as 3 curvas caminham juntas até que no terceiro dia a P90 dispara, mostrando um cenário muito otimista.
  No caso do 1022, a P90 já se distancia logo no primeiro dia previsto, enquanto a P10 apresenta um crescimento mais suave.
  Por fim o 1018, todas as curvas andam juntas até o final da previsão, mostrando pouca variação entre elas.
