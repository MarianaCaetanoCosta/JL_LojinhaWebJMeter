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