# Análise dos Focos de Queimadas no Brasil (2003 - Julho de 2024)

Este projeto realiza uma análise detalhada dos focos de queimadas no Brasil de 2003 até julho de 2024, utilizando a plataforma KNIME para processamento, transformação e visualização dos dados. A seguir, são descritas as etapas do fluxo de trabalho e os resultados obtidos.

## Objetivo

O objetivo principal desta análise é identificar padrões temporais e espaciais nos focos de queimadas ao longo do período estudado, com foco na identificação de meses críticos, variações interanuais e municípios mais afetados.

## Fluxo de Trabalho no KNIME

O fluxo de trabalho no KNIME foi estruturado em várias etapas, cada uma utilizando nós específicos para realizar tarefas de carregamento, limpeza, transformação, análise e visualização dos dados.

![Captura de tela 2024-08-25 155910](https://github.com/user-attachments/assets/232f27e9-d5e4-42d9-8ec1-1ddac359e5b9)

## Perguntas que queremos responder ao final da análise:</br>
**1. Qual foi o mês com mais focos de queimadas entre 2023 e julho de 2024?**</br>
**2. Quais anos tiveram os maiores picos de focos de queimadas em julho?**</br>
**3. Quais municípios registraram mais focos de queimadas desde 2003 até julho de 2024?**  </br>
**4. Quais estados foram mais afetados por queimadas em 2023?** </br>
**5. Como 2023 e 2024 se comparam em termos de focos de queimadas?** </br>
**6. Qual foi o ano com mais focos de queimadas entre 2003 e julho de 2024?**  </br>
</br>
## Fonte dos dados</br>
**terrabrasilis**</br>
**terrabrasilis**: [Mensal](https://dataserver-coids.inpe.br/queimadas/queimadas/focos/csv/mensal/Brasil/)</br>
**terrabrasilis**: [Anual](https://dataserver-coids.inpe.br/queimadas/queimadas/focos/csv/anual/Brasil_sat_ref/)</br>
</br>


### 1. Carregamento e Pré-processamento dos Dados

#### File Reader
Os dados foram importados usando dois nós **File Reader**, que carregaram arquivos de dados correspondentes ao período de 2003-2023 e aos meses de janeiro a julho de 2024, respectivamente.

#### Column Filter
Após o carregamento, foi utilizado o nó **Column Filter** para selecionar apenas as colunas relevantes para a análise, removendo quaisquer dados desnecessários que poderiam comprometer a eficiência e clareza das análises subsequentes.

#### Row Filter
O nó **Row Filter** foi aplicado para filtrar as observações específicas do satélite AQUA_M-T, focando nos dados de focos de queimadas capturados por este satélite.

Data Access</br>
![image](https://github.com/user-attachments/assets/0b73bf96-1634-4c48-a70f-314a65e15cc1)
![image](https://github.com/user-attachments/assets/6a609bbd-ce07-4a2b-983b-ca0d15dd6b51)



### 2. Data Merging e Transformações

#### Concatenate
Os conjuntos de dados de diferentes períodos foram integrados utilizando o nó **Concatenate**, criando um único dataset contínuo que engloba todo o período de interesse.</br>
![image](https://github.com/user-attachments/assets/3c6edc90-a542-4cc9-b059-f2ca031b10b6)


#### String to Date/Time
As colunas de data, inicialmente no formato string, foram convertidas para o formato de data padrão utilizando o nó **String to Date/Time**. Isso facilitou a manipulação e análise temporal dos dados.</br>
![image](https://github.com/user-attachments/assets/6ad01616-0b34-4f70-8abc-ed3fb4f2b24e)


#### Date&Time Part Extractor
Para extrair partes específicas da data, como ano e mês, o nó **Date&Time Part Extractor** foi utilizado, permitindo uma análise temporal mais granular.</br>
![image](https://github.com/user-attachments/assets/bbe40286-4720-4f97-b278-a8b8cdd63aa7)




### 3. Análises Estatísticas e Organização dos Dados

#### Table View e Statistics View
Antes de prosseguir com análises mais profundas, os nós **Table View** e **Statistics View** foram usados para revisar as distribuições dos dados, identificando quaisquer anomalias ou tendências iniciais.
</br>
TableView</br>
![image](https://github.com/user-attachments/assets/ce81bbd7-ad58-40e2-b676-e4e71944e816)
</br>
Statistics</br>
![image](https://github.com/user-attachments/assets/8b782637-878c-44e0-921a-385701b98a06)



#### GroupBy
Os dados foram agregados por diferentes dimensões (estado, município, ano, mês) utilizando o nó **GroupBy**. Isso permitiu a criação de tabelas sumarizadas que serviram de base para as visualizações.</br>
![image](https://github.com/user-attachments/assets/d4317e2e-9a27-4d13-bbf5-8eca34aa474e)


#### Crosstab
Utilizamos o nó **Crosstab** para criar tabelas cruzadas, permitindo visualizar a distribuição dos focos de queimadas ao longo do tempo e por diferentes regiões.</br>
![image](https://github.com/user-attachments/assets/33bae377-3365-43ac-86ce-641b7e1dcdb1)



### 4. Criação de Visualizações

As visualizações foram geradas para explorar os dados sob diversas perspectivas:

#### Meses com mais focos de queimadas de 2003 até 07/2024</br>
![Meses com mais focos de queimadas de 2003 até 07_2024](https://github.com/user-attachments/assets/9292650b-5a13-48a1-8e27-c57c3509ed87)



#### Os 10 meses de julho com mais focos de queimadas de 2003 - 07/2024</br>
![Os 10 meses de julho com mais focos de queimadas de 2003 - 07_2024](https://github.com/user-attachments/assets/291b9b83-84bf-4eeb-acaf-b94a67f3e7d8)


#### Os 20 municípios com mais focos de queimadas de 2003 até 07/2024</br>
![Os 20 muniípios com mais focos de queimadas de 2003 até 07_2024](https://github.com/user-attachments/assets/9a0f21ad-9df3-4d49-8a5f-109b5430a3aa)


#### Focos de queimadas por estados de 2003 até 07/2024</br>
![Focos de queimadas de 2003 até 07_2024](https://github.com/user-attachments/assets/56ad433c-b2ab-4467-a28f-4275a54e772b)


#### Estados com mais focos de queimadas em 2023</br>
![Estados com mais focos de queimadas em 2023](https://github.com/user-attachments/assets/de3647e8-e937-450c-aebe-d4f7b04502dd)


#### Comparação dos focos de queimadas entre 2023 e 2024</br>
![Foco de queimada de 2023 e 2024](https://github.com/user-attachments/assets/3b099d64-a854-4e0d-898f-ce0a8e403317)


#### Análise anual dos focos de queimadas de 2003 até 07/2024 por Estado</br>
![Focos de queimadas de 2003 até 07_2024 por Estado](https://github.com/user-attachments/assets/99725c33-b847-47ca-83dd-93e222df59d7)
</br>

## Conclusões

A análise foi conduzida para responder a algumas questões-chave sobre os padrões de focos de queimadas no Brasil:

**1. Quais meses registraram o maior número de focos de queimadas?**  
O mês de setembro foi o mais crítico, com mais de 1,43 milhões de focos, seguido por agosto e outubro. Estes meses correspondem à estação seca na maior parte do Brasil, quando as queimadas são mais prevalentes.

**2. Como os focos de queimadas em julho variaram ao longo dos anos?**  
Os anos de 2003, 2004 e 2005 destacaram-se com os maiores números de focos de queimadas em julho, indicando que esses anos foram excepcionalmente secos ou que houve menos controle sobre as queimadas.

**3. Quais municípios foram mais afetados pelas queimadas?**  
São Félix do Xingu liderou com mais de 106 mil focos desde 2003, seguido por Corumbá e Porto Velho, áreas conhecidas por atividades de desmatamento e pecuária intensiva.

**4. Quais estados foram mais impactados em 2023?**  
Pará registrou o maior número de focos de queimadas em 2023, com mais de 41 mil incidentes, refletindo a pressão contínua sobre as florestas nessa região.

**5. Como 2023 se compara a 2024 em termos de focos de queimadas?**  
Os dados indicam que 2023 teve significativamente mais focos de queimadas, especialmente em setembro. Isso pode ser um sinal de que as condições ambientais ou as políticas de manejo de queimadas foram menos eficazes em 2023.

**6. Qual foi o ano com maior incidência de queimadas entre 2003 e julho de 2024?**  
O ano de 2007 registrou o maior número de focos de queimadas, com quase 400 mil focos, destacando-se como um ano especialmente severo em termos de incêndios florestais.

## Como Executar

1. Clone este repositório.
2. Abra o arquivo de fluxo de trabalho no KNIME.
3. Certifique-se de que os arquivos de dados estejam no diretório correto.
4. Execute o fluxo de trabalho para reproduzir as análises e visualizações.

