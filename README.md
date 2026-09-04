# 🛒 Lojinha Web — Testes de Desempenho com JMeter

Projeto de **automação de testes de desempenho** da aplicação **Lojinha Web**, desenvolvido utilizando o **Apache JMeter**.

O projeto tem como objetivo demonstrar a criação, parametrização e execução de testes de **desempenho, carga e estresse**, utilizando usuários virtuais, dados parametrizados via CSV, gerenciamento de sessão, temporização e relatórios gráficos.

---

## 🎯 Objetivo

Avaliar o comportamento da aplicação Lojinha Web sob diferentes condições de utilização, analisando principalmente:

* Tempo de resposta das requisições;
* Comportamento da aplicação com múltiplos usuários simultâneos;
* Capacidade de processamento durante períodos prolongados;
* Comportamento da aplicação sob carga elevada;
* Quantidade de transações processadas por segundo;
* Evolução do número de usuários ativos;
* Identificação de possíveis pontos de degradação de desempenho.

---

## 🧪 Cenários automatizados

O plano de testes contempla as principais operações da aplicação:

1. Login;
2. Cadastro de produto;
3. Cadastro de componente;
4. Listagem de produtos;
5. Logoff.

---

# ▶️ Como executar

### 1. Instalar o Apache JMeter

Instale o Apache JMeter na versão utilizada no projeto.

### 2. Instalar o JMeter Plugins Manager

Instale o **JMeter Plugins Manager** e habilite os plugins necessários para os gráficos utilizados no projeto.

### 3. Clonar o projeto

```bash
git clone <URL_DO_REPOSITORIO>
```

### 4. Abrir o plano de teste

Abra o arquivo:

```text
Lojinha Web Testes.jmx
```

no Apache JMeter.

### 5. Conferir o arquivo de dados

Verifique se o caminho configurado no **CSV Data Set Config** corresponde ao arquivo:

```text
dados-teste-web.csv
```

### 6. Executar

Execute o plano de testes e acompanhe os resultados através dos relatórios configurados.

---

# 👩‍💻 Sobre o projeto

Projeto desenvolvido como parte do meu portfólio de **Qualidade de Software e Automação de Testes**, com foco na aplicação prática do Apache JMeter para criação e execução de testes de desempenho.

O projeto demonstra desde a **gravação das requisições e configuração do ambiente** até a **parametrização dos dados, execução de diferentes tipos de testes e análise dos resultados**.

---

⭐ **Projeto desenvolvido para estudos e demonstração de conhecimentos em testes de desempenho e automação com Apache JMeter.**
