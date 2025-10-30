# 🚗 Concessionária Web

Este projeto é um site para uma concessionária de veículos, desenvolvido com base em um wireframe responsivo.  
O objetivo é apresentar veículos disponíveis, informações institucionais e permitir o contato com a empresa.

---

## 📋 Estrutura do Projeto

- **Home:** Apresenta os veículos em destaque e as últimas ofertas.
- **Catálogo:** Lista de veículos com imagem, descrição e botão “Ler mais”.
- **Detalhes do Veículo:** Página individual com especificações técnicas e preço.
- **Contato:** Formulário para envio de mensagens e dados da concessionária.
- **Rodapé:** Links úteis, redes sociais e informações de contato.

---

## 🧱 Tecnologias Utilizadas

- **Frontend:** HTML5, CSS3, JavaScript
- **Backend:** PHP / Node.js (a definir)
- **Banco de Dados:** MySQL
- **Controle de Versão:** Git & GitHub

---

## 🧮 Estrutura de Banco de Dados

O banco de dados foi projetado com base no modelo DER a seguir, considerando as principais entidades:  
`clientes`, `veiculos`, `vendas`, `funcionarios`, e `fornecedores`.

---

## 🗺️ DER (Diagrama Entidade-Relacionamento)

```mermaid
erDiagram
    CLIENTE {
        INT id_cliente PK
        VARCHAR nome
        VARCHAR email
        VARCHAR telefone
        VARCHAR endereco
    }

    FUNCIONARIO {
        INT id_funcionario PK
        VARCHAR nome
        VARCHAR cargo
        DECIMAL salario
    }

    FORNECEDOR {
        INT id_fornecedor PK
        VARCHAR nome
        VARCHAR cnpj
        VARCHAR telefone
    }

    VEICULO {
        INT id_veiculo PK
        VARCHAR modelo
        VARCHAR marca
        YEAR ano
        DECIMAL preco
        VARCHAR cor
        INT id_fornecedor FK
    }

    VENDA {
        INT id_venda PK
        DATE data_venda
        DECIMAL valor_total
        INT id_cliente FK
        INT id_funcionario FK
        INT id_veiculo FK
    }

    CLIENTE ||--o{ VENDA : "realiza"
    FUNCIONARIO ||--o{ VENDA : "efetua"
    VEICULO ||--o{ VENDA : "pertence a"
    FORNECEDOR ||--o{ VEICULO : "fornece"
