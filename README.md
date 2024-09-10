# Plano de Teste - Lojinha Web



[TOC]

## Como Montar seu Script de Teste de Web



### Introdução

Este tutorial detalha o processo para criar e executar scripts de teste de automação para a Lojinha Web usando o JMeter. A seguir, você encontrará o passo a passo para configurar o plano de teste, criar grupos de usuários, gravar ações, configurar cookies e variáveis, e executar os testes.

---

### Passo 1: Criar o Plano de Teste

**Criar o Plano de Teste:**
   -   Crie um novo plano de teste chamado **Lojinha Web Testes** > Salve.

---

### Passo 2: Criar Grupo de Usuários

  **Configurar Grupo de Usuários para Login e Cadastro de Produto:**
    
   * Clique com o botão direito em **Lojinha Web Testes** > **Adicionar** > **Threads (users)** > **Grupo de Usuários**.

     
   -   Defina as configurações:
       - **Nome**: Login e Cadastro de Produto
       
       - **Número de usuários virtuais (threads)**: 1
       
         
       
       ![image-20240909194941527](C:\Users\maria\AppData\Roaming\Typora\typora-user-images\image-20240909194941527.png)

------

### Passo 3: Gravar o Passo a Passo do Teste

**Configurar o Servidor Proxy HTTP para Gravação:**
    
   - Navegue até: **Lojinha Web Testes > botão direito > Adicionar > Elementos que não são de Teste > Servidor HTTP Proxy**.

     

   -   Defina as configurações:
       -   **Nome**: `http://165.227.93.41/lojinha-web/v2/`
       -   **Porta**: `1234`



**Configurar o Filtro de Solicitação:**
    

  -   Aba **Test Plan Creation**:
      - **Controlador alvo**: Lojinha Web Testes > Login e Cadastro de Produto.
      
        
      
  -   Aba **Request Filtering**:
      -   **Padrões de URL a serem excluídos**: Adicione os padrões sugeridos.

![image-20240909195404602](C:\Users\maria\AppData\Roaming\Typora\typora-user-images\image-20240909195404602.png)



  -   Clique em **Iniciar**.
  -   Quando solicitado pelo Windows Firewall, clique em **OK**.
  -   A tela **Recorder: Transactions Control** será exibida.

------

### Passo 4 : Configurar Proxy no Navegador:

   -   Abra o Google Chrome e vá para: **Configurações > Pesquisar: proxy > "Abrir as configurações de proxy do navegador"**.

   

   -   Ative a opção **Usar servidor proxy** e defina:
       - **Endereço**: `localhost`
       
       - **Porta**: `1234`
       
         
       
   -   Clique em **Salvar**.

![image-20240909195947500](C:\Users\maria\AppData\Roaming\Typora\typora-user-images\image-20240909195947500.png)

![image-20240909200022853](C:\Users\maria\AppData\Roaming\Typora\typora-user-images\image-20240909200022853.png)

![image-20240909200039039](C:\Users\maria\AppData\Roaming\Typora\typora-user-images\image-20240909200039039.png)

------

### Passo 5: Realizar Testes na Lojinha Web

**Acessar a Lojinha Web e Executar o Teste:**
    
   1. Abra a aplicação Lojinha Web.        

      

   2. **Fazer Login:**        
      -   **Usuário**: `admin`

      -   **Senha**: `admin`

          

   3. **Adicionar um Produto:**
      	-   **Nome**: Fone de ouvido
            	-   **Valor**: 120,00
            	-   **Cor**: Preto, Dourado
            	-   Clique em **Salvar Produto**.

      ![image-20240909195058102](C:\Users\maria\AppData\Roaming\Typora\typora-user-images\image-20240909195058102.png)

      ![image-20240909195239151](C:\Users\maria\AppData\Roaming\Typora\typora-user-images\image-20240909195239151.png)

      

   4. **Adicionar um Componente ao Produto:** 
      	  -   **Nome**: Carregador USB
            	  -   **Quantidade**: 1
            	  -   Clique em **Salvar Componente**.

      ![image-20240909195142541](C:\Users\maria\AppData\Roaming\Typora\typora-user-images\image-20240909195142541.png)

      ![image-20240909195218557](C:\Users\maria\AppData\Roaming\Typora\typora-user-images\image-20240909195218557.png)

   5. **Listar Produtos Cadastrados.**

      

   6. **Fazer Logoff.**

      

7. **Finalizar a Gravação do Teste:**    
   * Pare a gravação do teste.

     

8. **Remova a configuração de Proxy do navegador**

   ![image-20240909200106351](C:\Users\maria\AppData\Roaming\Typora\typora-user-images\image-20240909200106351.png)

------

### Passo 5: Refatorar e Organizar a Gravação

**Limpar e Organizar a Gravação:**
* Exclua todas as gravações que não estão relacionadas à Lojinha Web.
* Renomeie os testes para um padrão de nomes mais claro.

------

### Passo 6: Adicionar Listeners e Executar o Teste

**Adicionar Listener para Visualizar Resultados:**    

- Navegue até: **Login e Cadastro de Produto > botão direito > Adicionar > Ouvinte > Ver Árvore de Resultados**.



**Executar o Teste:**    

- Clique no botão de execução para rodar o teste.

  

>  **Nota Importante:** Gerenciamento de Cookies
> O JMeter é "stateless" (não mantém estado) e, por padrão, não preserva os cookies da sessão, impedindo a visualização dos dados do produto e do componente. 



**Para corrigir isso Adicionar o Gerenciador de Cookies HTTP:**    

   - Navegue até: **Login e Cadastro de Produto > botão direito > Adicionar > Elemento de Configuração > Gerenciador de Cookie HTTP**.

     

**Executar o Teste e Verificar Resultados:**    

-   Execute o teste novamente e, para visualizar os dados do produto, acesse a aba **Response Body**.

------

### Passo 7: Criar Requisição Padrão

**Adicionar Padrão de Requisição HTTP:**
  - Navegue até: **Login e Cadastro de Produto > botão direito > Adicionar > Elemento de configuração > Padrões de Requisição HTTP**.

    

   -   Defina as configurações:
	      -   **Protocolo**: `http`
	            -   **Nome do Servidor ou IP**: `165.227.93.41`



> **Nota**: Em cada requisição, remova o protocolo e o nome do servidor para que todas as requisições sejam centralizadas no padrão definido.



![image-20240909194810673](C:\Users\maria\AppData\Roaming\Typora\typora-user-images\image-20240909194810673.png)

------

### Passo 8: Criar Variáveis de Configuração

**Adicionar Variáveis de Configuração:**

   - Navegue até: **Login e Cadastro de Produto > botão direito > Adicionar > Elemento de Configuração > Variáveis Definidas pelo Usuário**.

     

   -   Adicione as variáveis:
       -   `loginUsuario: admin`
       -   `senhaUsuario: admin`
       
       ![image-20240909194834028](C:\Users\maria\AppData\Roaming\Typora\typora-user-images\image-20240909194834028.png)



**Usar Variáveis nas Requisições:**

   -   Substitua os valores de login e senha:
       -   **Usuário**: `${loginUsuario}`
       -   **Senha**: `${senhaUsuario}`

![image-20240909194851880](C:\Users\maria\AppData\Roaming\Typora\typora-user-images\image-20240909194851880.png)



**Executar o Teste com as Variáveis Configuradas:**

   - Execute o teste e, para visualizar os dados do produto, acesse a aba **Response Body**.

     

![image-20240909194914678](C:\Users\maria\AppData\Roaming\Typora\typora-user-images\image-20240909194914678.png)



# Refatorar



### Cadastrar usuários virtuais

1. Login com Cadastro de Produto
1. Cadastrar a partir de 5 usuários virtuais

![image-20240910004920491](C:\Users\maria\AppData\Roaming\Typora\typora-user-images\image-20240910004920491.png)



### Cabeçalho dos dados

1. Abra um bloco de notas e cadastro conforme informações abaixo:

* login;senha;nomeProduto;valorProduto;coreProduto;componenteNome;componenteQuantidade
* admin;admin;iPhone;200,00;Azul;Carregador;1
* admin;admin;Macbook Pro;6999,99;Cinza;Bateria;1
* admin;admin;Apple Watch;3599,99;Vermelho;Pelicula;1
* admin;admin;iPad 10a Geracao;2020,00;Branco;Capa De Proteção;1
* admin;admin;Relogio;455,80;Dourado;Pulseira;1

salvar o arquivo como dados-teste.api.csv

![image-20240910121438138](C:\Users\maria\AppData\Roaming\Typora\typora-user-images\image-20240910121438138.png)

### Elemento de Configuração - CSV Data Set Config

1. Clique com o botão direito em **Login com** **Cadastro de Produto** > Adicionar > Elemento de Configuração > CSV Data Set Config

![image-20240910005213503](C:\Users\maria\AppData\Roaming\Typora\typora-user-images\image-20240910005213503.png)

### Variáveis do ambiente

1. Clique com o botão direito em **Variáveis do ambiente** > desabilitar

![image-20240910005246701](C:\Users\maria\AppData\Roaming\Typora\typora-user-images\image-20240910005246701.png)

### Fazer Login

1. Na aba: **Parameters** alteram as variáveis

![image-20240910005648811](C:\Users\maria\AppData\Roaming\Typora\typora-user-images\image-20240910005648811.png)

### Salvar Produto

![image-20240910010740053](C:\Users\maria\AppData\Roaming\Typora\typora-user-images\image-20240910010740053.png)



### Adicionar componente

![image-20240910010806983](C:\Users\maria\AppData\Roaming\Typora\typora-user-images\image-20240910010806983.png)



### Adicionar temporizador

Clique com o botão direito em **Login com Cadastro de usuário** > Adicionar > Temporizador > Temporizador Aleatório Gaussiano

![image-20240910010948599](C:\Users\maria\AppData\Roaming\Typora\typora-user-images\image-20240910010948599.png)

### Executar Testes

![image-20240910011319523](C:\Users\maria\AppData\Roaming\Typora\typora-user-images\image-20240910011319523.png)



# Implementar Relatórios



### Instalação Plugin

1. Fazer Download [Jmeter Plugin Manager](https://jmeter-plugins.org/wiki/PluginsManager/)

2. Salvar na pasta **apache-jmeter-5.6.3\lib\ext**

3. Reinicie o **Jmeter** para reconhecer o plugin

   

### Habilitação do Plugin

1. Abra o Jmeter > Opções > Jmeter Plugin Manager > Aba: Avaliable Plugins > habilitar: 3 Basic Graphs > Apply changes and Restart Jmeter > ele vai baixar os arquivos e reiniciar o Jmeter

![image-20240910094807719](C:\Users\maria\AppData\Roaming\Typora\typora-user-images\image-20240910094807719.png)

### Abra o Projeto "**Lojinha Web Testes.jmx**"

1. clique com o botão direito sobre **"Ver Árvore de Resultados"** > Desabilite 

![image-20240910112153754](C:\Users\maria\AppData\Roaming\Typora\typora-user-images\image-20240910112153754.png)

### Adicionar **Ouvintes** de gráficos importantes do plugin

1. Clique com o botão direito em **Lojinha com Cadastro de Produto** > Adicionar > Ouvinte
   1. Relatório Agregado
   2. Relatório De Sumário
   3. Jp@gc - Active Thereads Over Time
   4. Jp@gc - Response Times Over Time
   5. Jp@gc - Transactions per Second



### Configurar os Ouvintes para exibir resultado em 100ms

1. Clique no relatório **Jp@gc - Active Thereads Over Time** > Aba: Settings > Group timeline values for: 100ms

2. Clique no relatório **Jp@gc - Response Times Over Time** > Aba: Settings > Group timeline values for: 100ms

3. Clique no relatório **Jp@gc - Transactions per Second** > Aba: Settings > Group timeline values for: 100ms

   

### Configuração dos testes de **Desempenho**, **Carga** e **Estresse**

#### Teste de Desempenho

* **Objetivo:** Validar que a aplicação funciona bem quando nossos usuários a utiliza.
* **Cenário:** Cadastro de Produto
* **Quantidade de Usuários:** 50 usuários simultâneos
* **Tempo de Execução:** N/A
* **Resultado Esperado:** Tempo de carregamento máximo de 3 segundos



* **Configuração:**

  * Login com Compra de Produtos
    * Propriedade do Usuário Virtual
      * Número de Usuários Virtuais (thereads): 50
      * Tempo de inicialização (em segundos): 3
      * Contador de Iteração: 1

  ![image-20240910112407165](C:\Users\maria\AppData\Roaming\Typora\typora-user-images\image-20240910112407165.png)

  

#### Teste de Carga

* **Objetivo:** Validar que durante todo o dia nacional das compras, nossos usuários tenham uma experiência veloz do uso do software.
* **Cenário:** Compra de Produto
* **Quantidade de Usuários:** 50 usuários simultâneos
* **Tempo de Execução:** 24 horas
* **Resultado Esperado:** Tempo de carregamento máximo de 3 segundos



* **Configuração:**

  * Login com Compra de Produtos

    * Propriedade do Usuário Virtual

      * Número de Usuários Virtuais (thereads): 50

      * Tempo de inicialização (em segundos): 3

      * Contador de Iteração: 1

      * Habilite: Agendador

        * Duração (segundos): 86400

        * Atraso para início (segundos): 

![image-20240910112432054](C:\Users\maria\AppData\Roaming\Typora\typora-user-images\image-20240910112432054.png)

#### Teste de Estresse

* **Objetivo:** Descobrir quais são os limites da aplicação e sua infraestrutura enquanto é utilizada de maneira excessiva.

* **Cenário:** Pesquisa de Produto

* **Quantidade de Usuários:** N/A

* **Tempo de Execução:** N/A

* **Resultado Esperado:** N/A

  

* **Configuração:**

  * Login com Compra de Produtos

    * Propriedade do Usuário Virtual

      * Número de Usuários Virtuais (thereads): 999999999999999999999999999

      * Tempo de inicialização (em segundos): 999999999

      * Contador de Iteração > habilite Infinito

        

  ![image-20240910112527395](C:\Users\maria\AppData\Roaming\Typora\typora-user-images\image-20240910112527395.png)



### Configuração dos dados CSV

1. Como você tem 5 dados cadastrados o Jmeter vai começar a reaproveitar os dados para os testes duplicando os registros, no nosso caso não tem problema.
2. Para testes mais robustos será necessários criar 50 dados para que não haja duplicidade de registros.



### Salve as configurações

### Execute os Testes e acompanhar resultados

1. Limpe os resultados dos relatórios
2. Execute o Teste



#### Relatório Agregado

![image-20240910120519551](C:\Users\maria\AppData\Roaming\Typora\typora-user-images\image-20240910120519551.png)

#### Relatório de sumário

![image-20240910121018921](C:\Users\maria\AppData\Roaming\Typora\typora-user-images\image-20240910121018921.png)

#### jp@gc - Active Threads Over Time

![image-20240910121054315](C:\Users\maria\AppData\Roaming\Typora\typora-user-images\image-20240910121054315.png)

#### jp@gc - Response Times Over Time

![image-20240910121110082](C:\Users\maria\AppData\Roaming\Typora\typora-user-images\image-20240910121110082.png)

#### jp@gc - Transactions per Second

![image-20240910121127118](C:\Users\maria\AppData\Roaming\Typora\typora-user-images\image-20240910121127118.png)