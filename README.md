jmeter-beginner-tutorial
# README #


### Table of Contents
* [Introdução](#1.Introdução)
* [Documentação](#2.Documentação)
* [Projeto](#3.Projeto)
    * [Pré-requisitos](#3.1.Pré-requisitos)
    * [Guia e Tutorial](#3.2.GuiaeTutorial)
    * [Pré-requisitos](#3.1.Pré-requisitos)


## 1. Introdução

Este repositório contém um tutorial do **JMeter** . 

### 2. Documentação

### 2.1. Diagramas ###

* n/a


## 3. Projeto

### 3.1. Pré-requisitos ###

* Java JDK 8
* JMeter ( 3.3 ou 4.0 ou 5.0)


### 3.2. Guia e Tutorial ###

#### 3.2.1 Thread Groups, HTTP Request, View Results in Table, View Results Tree e Summary Report ####
* Test Plan -  New project has already a default Test Plan
* Diagramas
    * Deploy Diagram

```image-file
   localhost      www.digitalocean.com
  +--------+        +--------+
 /        /|       /        /|
+--------+ |      +--------+ |
| JMeter | | ---> |        | |--o  :443/community/tutorials/how-to-use-apache-jmeter-to-perform-load-testing-on-a-web-server
| Script |/       |        |/
+--------+        +--------+
```

* Criando Grupo de Usuários: Add >> Threads (Users) >> Thread Group
    * Properties (importantes):
        * "Number of Thread Users": [2] Número de usuários simultâneos. Exemplo: 2
        * "Ramp-up Period (in seconds)": [10] Quantidade de tempo de cada ciclo antes do incremento de usuários. Exemplo: 10 seconds
        * "Loop Count": [100] Contador de vezes. Exemplo: 100 vezes
		* Comentário: Iniciando com "Number of Thread Users" usuário simultâneo, a cada "Ramp-up Period (in seconds)" segundos acrescenta mais "Number of Thread Users" usuários até a condição de parada "Loop Count"
* Criando Requisição HTTP: Add >> Sampler >> HTTP Request
    * Properties (importantes):
        * "Web Server - Server Name or IP Address": [www.digitalocean.com] Endereço IP do servidor
        * "Web Server - Protocol": [https] Nome do protocolo. Não colocar o protocolo junto com o servidor
        * "HTTP Request - Method": [GET] chamada get do protocolo. Exemplo: www.digitalocean.com
        * "Path": Caminho da página. [/community/tutorials/how-to-use-apache-jmeter-to-perform-load-testing-on-a-web-server] caminho do endereço que vem logo após o servico
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
	* [How to Use Jmeter](https://www.digitalocean.com/community/tutorials/how-to-use-apache-jmeter-to-perform-load-testing-on-a-web-server)
* Source Code Example:
    * [01 - Thread Groups HTTP Request View Results in Table.jmx](src/01%20-%20Thread%20Groups%20HTTP%20Request%20View%20Results%20in%20Table.jmx)


#### 3.2.2. Response Assertions, Duration Assertions, Size Assertions, HTML and XML Formats, XPATH e Assertions Results ####
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
* Source Code Example:
    * [02 - Assertions (Response Code Duration Size Contents) e Listener Assertions Result](src/02%20-%20Assertions%20(Response%20Code%20Duration%20Size%20Contents)%20e%20Listener%20Assertions%20Results.jmx)


#### 3.2.3.  Listeners - View results in (Table, Tree, Aggregate Report, Graph Result, Summary Report)  ####
* O que são os listener? São elementos que coletam e retornam informações sobre o teste, usados para visualizar o resultado de um teste e suas métricas
* O que é "latencia"? É o tempo até que o primeiro byte de resposta seja apresentado
* O que é "tempo de resposta"? É o tempo decorrido desde o início da requisição, passando pelo momento onde começa ocorrer a entrega dos bytes da requisição até o último byte ser recebido
* O que é "connect time"? É o tempo gasto durante o procedimento de conexão entre o client (JMeter) e o servidor(Normalmente HTTP Server). Ele não contempla o tempo do serviço de entrega dos bytes, porém pode ser um indicativo de problemas de conexão. 
* Criando Grupo de Usuários: Add >> Threads (Users) >> Thread Group
    * "Number of Thread Users": [5] Número de usuários simultâneos
    * "Ramp-up Period (in seconds)": [1] Quantidade de tempo de cada ciclo antes do incremento de usuários
    * "Loop Count": [100] Contador de vezes
* Criando Requisição HTTP: Add >> Sampler >> HTTP Request
    * "Web Server - Server Name or IP Address": [www.digitalocean.com] Endereço IP do servidor
    * "Web Server - Protocol": [https] Nome do protocolo. Não colocar o protocolo junto com o servidor
    * "HTTP Request - Method": [GET] chamada get do protocolo
    * "Path": Caminho da página. [/community/tutorials/how-to-use-apache-jmeter-to-perform-load-testing-on-a-web-server] caminho do endereço que vem logo após o servico
* Listener "View Results in Table": >> Add >> Listener >> View Results in Table
	* Mostra no formato tabular todas as métricas de cada uma das execução
* Listener "View Results Tree": >> Add >> Listener >> View Results Tree
	* Mostra no formato hierarquico os detalhes de uma execução:
		* requisição "Request"
		* resposta "Response"
		* amostra do resultado "Sample Result"
* Listener "Aggregate Report": >> Add >> Listener >> Summary Reports
	* Mostra de forma agrupada as métricas de todas as execuções
		* "\# Samples": Número de amostras, Tempos mínimos, médios e máximo de cada requisição, quantidade de bytes trafegados, latência, etc
* Listener "Summary Report": >> Add >> Listener >> Summary Report
    * Mostra de forma agrupada as métricas do relatório
* Listener "Graph Results": >> Add >> Listener >> Graph Results
    * Mostra on-line/real-time as métricas e resultados dos tests
    * Configure: [ ] Data; [X] Average; [ ] Medium; [ ] Deviation; [X] Throughput;
* "Simple Data Writer": >> Add >> Listener >> Simple Data Writer
    * Salva diversas métricas em arquivo
	* "View Results to File": [04 - Sample Data Writer.csv]
    * "Errors": [ ] 
    * "Success": [ ]
	* "Configure": ...; [X] Save Elapsed Time; ...
* Referências:
    * [JMeter Beginner Tutorial 4 - How to use Listeners](https://www.youtube.com/watch?v=5FyVKVAqEJo&index=4&list=PLhW3qG5bs-L-zox1h3eIL7CZh5zJmci4c)
* Source Code Example:
    * [03 - Listeners - View Results in (Table, Tree, Aggregate Report, Graph Result, Summary Report, Sample Data Writer)](src/02%20-%20Assertions%20(Response%20Code%20Duration%20Size%20Contents)%20e%20Listener%20Assertions%20Results.jmx)
* Screen Captured Example:
    * [Screen Captured Examples](doc/Listener/README.md)

#### 3.2.4. Gravar interação, Record UI Interaction using JMeter, Badboy e BlazeMeter (Chrome Plugin) ####
* Step-by-Step recording UI Test Using Blazemeter
    * Step 1: Record a Test
	* Step 2: Export as JMeter (.jmx) Script
	* Step 3: Open the Script in JMeter
	* Step 4: Add Listeners
	* Step 5: Run and Validate
* Referências:
    * [JMeter Beginner Tutorial 5 - How to record a UI (web) Test](https://www.youtube.com/watch?v=JI99ZOuI5tQ&index=5&list=PLhW3qG5bs-L-zox1h3eIL7CZh5zJmci4c)


#### 3.2.5. Como criar um teste no banco de dados ####
* Step-by-Step creating database connection
    * Step 1: Add sqldatabase driver to JMeter lib folder | Restart JMeter
	* Step 2: Add Thread Groups
	* Step 3: Add JDBC Conn Config | Provide details of database (dica www.db4free.net)
	* Step 4: Add JDBC Request
	* Step 5: Add Listener
	* Step 6: Run and validate
* Referências:
    * [JMeter Beginner Tutorial 6 - How to create a Database Test Plan](https://www.youtube.com/watch?v=oy53KAKHpts&index=6&list=PLhW3qG5bs-L-zox1h3eIL7CZh5zJmci4c)


#### 3.2.5. Como executar JMeter sem interface gráfica ####
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
	
