# PRD — Gerenciador de Leituras

## 1. Visão Geral

**Nome do produto:** Gerenciador de Leituras  
**Autor:** [Seu Nome Completo]  
**Data:** Março de 2026  
**Versão:** 1.0  

### Objetivo
Criar uma aplicação web responsiva que permita ao usuário organizar sua estante pessoal de livros, acompanhar o progresso de leitura e descobrir novas obras.

---

## 2. Personas

### 2.1 Leitor Casual — João, 22 anos
- Estudante universitário que quer controlar os livros que leu e quer ler
- Usa principalmente o celular
- Quer uma interface simples e rápida

### 2.2 Leitor Ávido — Maria, 35 anos
- Lê mais de 20 livros por ano
- Quer escrever resenhas e atribuir notas
- Acessa pelo computador e tablet

---

## 3. Funcionalidades

### 3.1 Funcionalidades Obrigatórias (MVP)

| ID | Funcionalidade | Prioridade |
|----|---------------|-----------|
| F01 | Cadastrar livro com título, autor, gênero e status | Alta |
| F02 | Listar livros em cards com filtro por status | Alta |
| F03 | Editar informações de um livro | Alta |
| F04 | Excluir livro da estante | Alta |
| F05 | Buscar dados automáticos pelo ISBN via Open Library | Alta |
| F06 | Marcar livro como favorito | Média |
| F07 | Escrever resenha e dar nota (1-5 estrelas) | Média |
| F08 | Dashboard com estatísticas de leitura | Média |
| F09 | Cadastro de perfil com preenchimento automático por CEP | Média |
| F10 | Filtrar livros por gênero | Baixa |

### 3.2 Regras de Negócio

- **RN01:** Um livro deve ter obrigatoriamente título e autor
- **RN02:** O ISBN deve seguir o formato ISBN-10 ou ISBN-13
- **RN03:** A avaliação deve ser um número inteiro entre 1 e 5
- **RN04:** Um livro com status "Lido" pode ter data de conclusão
- **RN05:** Um livro com status "Lendo" pode ter data de início
- **RN06:** Gêneros são cadastrados separadamente e vinculados aos livros

---

## 4. Requisitos Não Funcionais

- A aplicação deve ser responsiva (mobile, tablet, desktop)
- Tempo de carregamento inicial inferior a 3 segundos
- Funcionar nos navegadores: Chrome, Firefox, Edge (versões atuais)
- Deploy no GitHub Pages

---

## 5. Fora do Escopo (v1.0)

- Login e autenticação de usuários
- Compartilhamento de estante entre usuários
- Recomendação de livros por IA
- Importação de dados do Goodreads
