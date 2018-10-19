jmeter-beginner-tutorial

# README #


## 1. Introdução ##

Este repositório contém um tutorial do **JMeter** . 

### 2. Documentação ###

### 2.1. Diagramas ###

```image-file
n/a
```


## 3. Projeto ##

### 3.1. Pré-requisitos ###

* Java JDK 8
* JMeter ( 3.3 ou 4.0)


### 3.6. Guia e Tutorial ###

#### 3.6.1 Thread Groups, HTTP Request, View Results in Table, View Results Tree e Summary Report ####
* Test Plan -  New project has already a default Test Plan
* Criando Grupo de Usuários: Add >> Threads (Users) >> Thread Group
    * Properties (importantes):
        * "Number of Thread Users": Número de usuários simultâneos. Exemplo: 1
        * "Ramp-up Period (in seconds)": Quantidade de tempo de cada ciclo antes do incremento de usuários. Exemplo: 20 seconds
        * "Loop Count": Contador de vezes. Exemplo: 5 vezes
* Criando Requisição HTTP: Add >> Sampler >> HTTP Request
    * Properties (importantes):
        * "Server Name or IP Address": Endereço IP do servidor
        * "HTTP Request - Method": [GET] chamada get do protocolo. Exemplo: lifecharger.org
        * "Path": Caminho da página. Exemplo: /look-at-the-other-side
* Relatórios da execução ou Listeners
    * [Thread Group] >> Add >> Listener >> View Results in Table
        * Mostra no formato tabular todas as métricas de cada uma das execução
    * [Thread Group] >> Add >> Listener >> View Results Tree
        * Mostra no formato hierarquico os detalhes de uma execução:
            * requisição "Request"
            * resposta "Response"
            * amostra do resultado "Sample Result"
    * [Thread Group] >> Add >> Listener >> Summary Reports
        * Mostra de forma agrupada as métricas de todas as execuções
            * "\# Samples": Número de amostras, Tempos mínimos, médios e máximo de cada requisição, quantidade de bytes trafegados, latência, etc
* Executando o teste ( Menu >> Run >> Start ) ou clique no botão play
* Limpar métricas de execução( Menu >> Run >> Clear ) ou ( Menu >> Run >> Clear )
    * Limpa as métricas de execução dos Listener ou Relatórios
* Referências:
    * [JMeter Beginner Tutorial 2 - How to create first Jmeter Test](https://www.youtube.com/watch?v=8loLHbhfyh0&index=2&list=PLhW3qG5bs-L-zox1h3eIL7CZh5zJmci4c)


#### 3.6.2. Response Assertions, Duration Assertions, Size Assertions, HTML and XML Formats, XPATH e Assertions Results ####
* O que é assertions? São validações realizadas sobre as respostas. Pode ser validado resultados do cabeçalho HTTP, conteúdos da página, variaveis do JMeter, etc.
* Criando um assertions sobre Response Code do Cabeçalho HTTP: Add >> Assertions >> Response Assertions
    * Properties (importantes):
        * "Apply to: ... [X] Main sample only ...": 
        * "Response Field to Test: ... [X] Response Code ...": 
        * "Pattern match rule: ... [X] Equals ...": 
* Criando um relatório com Assertions Results: Add >> Listener >> Assertions Results
    * Properties (importantes):
        * "Apply to: ... [X] Main sample only ...": 
        * "Response Field to Test: ... [X] Response Code ...": 
        * "Pattern match rule: ... [X] Equals ...": 
* Criando um assertions sobre o tempo de duração da requisição HTTP: Add >> Assertions >> Duration Assertion
    * Properties (importantes):
        * "Duration in milliseconds":  Tempo máximo de duração **de cada requisição**. Exemplo: 2000 ms. No lister "View Results in Table" a coluna "Sample Time(ms)" traz o tempo 
        * "Response Field to Test: ... [X] Response Code ...": 
        * "Pattern match rule: ... [X] Equals ...": 
* Criando um assertions sobre o tamanho da requisição HTTP: Add >> Assertions >> Size Assertion
    * Properties (importantes):
        * "Apply to: ... [X] Main sample only ...": Refere-se ao fluxo principal
        * "Response size field to test: ... [X] Full response ...": 
        * "Size in bytes: ... [=] Equals ...": Igual a. Exemplo: 5000
* Criando um assertions sobre o HTML da página: Add >> Assertions >> HTML Assertion
    * Properties (importantes):
        * "Apply to: ... [X] Main sample only ...": Refere-se ao fluxo principal
        * "Response size field to test: ... [X] Full response ...": 
        * "Size in bytes: ... [=] Equals ...": Igual a. Exemplo: 5000
* Criando um assertions sobre o XML da página: Add >> Assertions >> XML Assertion
* Criando um assertions sobre o XPATH da página: Add >> Assertions >> XPATH Assertion
    * Properties (importantes):
        * "Apply to: ... [X] Main sample only ...": Refere-se ao fluxo principal
        * "XPATH assertion:": XPATH esperado na resposta. Exemplo: 
* Referências:
    * [JMeter Beginner Tutorial 3 - How to use Assertions](https://www.youtube.com/watch?v=mXhC9CtQBC8&list=PLhW3qG5bs-L-zox1h3eIL7CZh5zJmci4c&index=3)


#### 3.6.3.  Listeners ####
* O que são os listener? São elementos que coletam e retornam informações sobre o teste, usados para visualizar o resultado de um teste e suas métricas
* O que é latencia? É o tempo até que o primeiro byte de resposta seja apresentado
* Listener "View Results in Table": >> Add >> Listener >> View Results in Table
	* Mostra no formato tabular todas as métricas de cada uma das execução
* Listener "View Results Tree": >> Add >> Listener >> View Results Tree
	* Mostra no formato hierarquico os detalhes de uma execução:
		* requisição "Request"
		* resposta "Response"
		* amostra do resultado "Sample Result"
* Listener "Summary Report": >> Add >> Listener >> Summary Report
    * Mostra de forma agrupada as métricas do relatório
* Listener "Aggregate Report": >> Add >> Listener >> Summary Reports
	* Mostra de forma agrupada as métricas de todas as execuções
		* "\# Samples": Número de amostras, Tempos mínimos, médios e máximo de cada requisição, quantidade de bytes trafegados, latência, etc
* Listener "Graph Results": >> Add >> Listener >> Graph Results
    * Mostra on-line/real-time as métricas e resultados dos tests
* "Simple Data Writer": >> Add >> Listener >> Simple Data Writer
    * Mostra diversas mét
* Referências:
    * [JMeter Beginner Tutorial 4 - How to use Listeners](https://www.youtube.com/watch?v=5FyVKVAqEJo&index=4&list=PLhW3qG5bs-L-zox1h3eIL7CZh5zJmci4c)


#### 3.6.4. Gravar interação, Record UI Interaction using JMeter, Badboy e BlazeMeter (Chrome Plugin) ####
* Step-by-Step recording UI Test Using Blazemeter
    * Step 1: Record a Test
	* Step 2: Export as JMeter (.jmx) Script
	* Step 3: Open the Script in JMeter
	* Step 4: Add Listeners
	* Step 5: Run and Validate
* Referências:
    * [JMeter Beginner Tutorial 5 - How to record a UI (web) Test](https://www.youtube.com/watch?v=JI99ZOuI5tQ&index=5&list=PLhW3qG5bs-L-zox1h3eIL7CZh5zJmci4c)


#### 3.6.5. Como criar um teste no banco de dados ####
* Step-by-Step creating database connection
    * Step 1: Add sqldatabase driver to JMeter lib folder | Restart JMeter
	* Step 2: Add Thread Groups
	* Step 3: Add JDBC Conn Config | Provide details of database (dica www.db4free.net)
	* Step 4: Add JDBC Request
	* Step 5: Add Listener
	* Step 6: Run and validate
* Referências:
    * [JMeter Beginner Tutorial 6 - How to create a Database Test Plan](https://www.youtube.com/watch?v=oy53KAKHpts&index=6&list=PLhW3qG5bs-L-zox1h3eIL7CZh5zJmci4c)


#### 3.6.5. Como executar JMeter sem interface gráfica ####
* Command Line:
```bash
jmeter -n -t <Jmeter_Script_Location> -l <JMeter_ResultFile_Location>
```

* Referências:
    * [JMeter Beginner Tutorial 7 - How to run jmeter from Command Line - non GUI mode](https://www.youtube.com/watch?v=K26q5VgwLKk&list=PLhW3qG5bs-L-zox1h3eIL7CZh5zJmci4c&index=7)

* Plugins 
    * bzm-parallel-0.7 "BlazeMeter Parallel Controle"
	* Summary Report    : ~/result/result_${__time(yyyy-MM-dd HHmmss)}
	* Simple Data Writer: ~/erros/erros_${__time(yyyy-MM-dd HHmmss)}
	