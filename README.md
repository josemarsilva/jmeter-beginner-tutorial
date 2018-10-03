jmeter-beginner-tutorial

# README #


## 1. Introdução ##

Este repositório contém um tutorial do **JMeter** . 

### 2. Documentação ###

### 2.1. Diagrama de Caso de Uso (Use Case Diagram) ###

```image-file
n/a
```

### 2.2. Diagrama de Implantação (Deploy Diagram) ###

```image-file
n/a
```

### 2.3. Diagrama de Atividades (Activity Diagram) ###

```image-file
n/a
```


### 2.4. Diagrama Modelo Banco de Dados (Database Data Model) ###

```image-file
n/a
```


## 3. Projeto ##

### 3.1. Pré-requisitos ###

* Java JDK 8
* JMeter ( 3.3 ou 4.0)


### 3.6. Guia e Tutorial ###

#### 01 - Thread Groups, HTTP Request, View Results in Table, View Results Tree e Summary Report
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
* Exemplos:
    * [./src/01 - Thread Groups HTTP Request View Results in Table.jmx]

## Referências ##

* [JMeter Beginner Tutorial 2 - How to create first Jmeter Test](https://www.youtube.com/watch?v=8loLHbhfyh0&index=2&list=PLhW3qG5bs-L-zox1h3eIL7CZh5zJmci4c)
* 
