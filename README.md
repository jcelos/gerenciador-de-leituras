# gerenciador-de-leituras

**Autor:** João Paulo Vasconcelos

Este projeto tem como objetivo implementar progressivamente uma aplicacao web para organizar leituras pessoais (livros que quero ler, estou lendo e ja li), com cadastro, edicao, avaliacao e filtros.

O frontend foi desenvolvido com HTML, CSS, Bootstrap e JavaScript. O backend e simulado com API Fake usando JSON Server.

## Documentacao do Projeto

Para entender regras de negocio, escopo e estrutura tecnica, consulte:

- [Product Requirements Document (PRD)](docs/prd.md)
- [Especificacao Tecnica (SPEC)](docs/spec.md)

## Design

https://stitch.withgoogle.com/projects/11086232145645190116

## Site em Producao

Em desenvolvimento.

## Tecnologias e Dependencias

- Framework CSS: Bootstrap 5
- JavaScript: jQuery
- API Fake: JSON Server
- Qualidade de codigo: ESLint e Prettier
- Estilizacao: Sass (SCSS)

## Checklist | Indicadores de Desempenho (ID) dos Resultados de Aprendizagem (RA)

### RA1 - Framework CSS e responsividade
- [ ] ID 01 - Protótipo mobile e desktop
- [ ] ID 02 - Layout responsivo com framework CSS
- [ ] ID 03 - Layout responsivo com CSS puro
- [ ] ID 04 - Componentes de framework (card, button, modal, carousel)
- [ ] ID 05 - Uso de unidades relativas
- [ ] ID 06 - Design System consistente
- [ ] ID 07 - Uso de Sass com variaveis/mixins/funcoes
- [ ] ID 08 - Tipografia responsiva
- [ ] ID 09 - Responsividade de imagens
- [ ] ID 10 - Otimizacao de imagens

### RA2 - Formularios e validacoes
- [ ] ID 11 - Validacao HTML nativa
- [ ] ID 12 - Validacao com REGEX
- [ ] ID 13 - Uso de checkbox/radio/select
- [ ] ID 14 - Persistencia com Web Storage

### RA3 - Ferramentas de desenvolvimento
- [x] ID 15 - Node.js e NPM configurados
- [x] ID 16 - Versionamento com Git/GitHub e .gitignore
- [x] ID 17 - README padronizado com checklist
- [x] ID 18 - Organizacao modular de arquivos
- [x] ID 19 - ESLint e Prettier configurados

### RA4 - Bibliotecas JavaScript
- [ ] ID 20 - Uso de jQuery para interatividade
- [ ] ID 21 - Plugin jQuery relevante (ex.: mask)

### RA5 - Requisicoes assincronas
- [ ] ID 22 - Requisicoes para API Fake para persistencia
- [ ] ID 23 - Requisicoes para API Fake para exibicao
- [ ] ID 24 - Requisicoes para API publica

## Manual de Execucao

1. Clonar o repositorio:
```bash
git clone https://github.com/jcelos/gerenciador-de-leituras.git
cd gerenciador-de-leituras
```

2. Instalar dependencias:
```bash
npm i
```

3. Executar API Fake:
```bash
npm run api
```

4. Em outro terminal, executar compilacao SCSS (opcional durante desenvolvimento):
```bash
npm run sass
```

5. Abrir as paginas HTML no navegador (ou com Live Server no VS Code).

## Telas da Aplicacao

- `lp.html` - Landing page
- `login.html` - Login
- `index.html` - Dashboard inicial
- `estante.html` - Lista de livros
- `cadastro.html` - Cadastro/edicao de livro
- `detalhes.html` - Detalhes do livro
- `perfil.html` - Perfil/preferencias
