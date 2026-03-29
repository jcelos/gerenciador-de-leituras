# SPEC — Especificação Técnica | Gerenciador de Leituras

## 1. Modelo de Dados

### Entidade: Livro

```json
{
  "id": 1,
  "titulo": "O Senhor dos Anéis",
  "autor": "J.R.R. Tolkien",
  "generoId": 2,
  "status": "lido",
  "avaliacao": 5,
  "favorito": true,
  "isbn": "9788533613379",
  "paginas": 1200,
  "capaUrl": "https://covers.openlibrary.org/b/isbn/9788533613379-L.jpg",
  "dataInicio": "2026-01-10",
  "dataConclusao": "2026-02-20",
  "resenha": "Uma obra épica e inesquecível.",
  "criadoEm": "2026-01-10T10:00:00Z"
}
```

**Campos:**
| Campo | Tipo | Obrigatório | Descrição |
|-------|------|-------------|-----------|
| id | number | auto | Identificador único |
| titulo | string | ✅ | Título do livro |
| autor | string | ✅ | Nome do autor |
| generoId | number | ✅ | FK para Gênero |
| status | enum | ✅ | `quero-ler` \| `lendo` \| `lido` |
| avaliacao | number | ❌ | 1 a 5 (apenas se status = lido) |
| favorito | boolean | ❌ | Padrão: false |
| isbn | string | ❌ | ISBN-10 ou ISBN-13 |
| paginas | number | ❌ | Número de páginas |
| capaUrl | string | ❌ | URL da imagem da capa |
| dataInicio | date | ❌ | Quando começou a ler |
| dataConclusao | date | ❌ | Quando terminou |
| resenha | string | ❌ | Texto livre |
| criadoEm | datetime | auto | Timestamp de criação |

---

### Entidade: Gênero

```json
{
  "id": 1,
  "nome": "Fantasia",
  "cor": "#8B5CF6"
}
```

**Campos:**
| Campo | Tipo | Obrigatório | Descrição |
|-------|------|-------------|-----------|
| id | number | auto | Identificador único |
| nome | string | ✅ | Nome do gênero |
| cor | string | ✅ | Cor hexadecimal para badge |

---

### db.json inicial (JSON Server)

```json
{
  "livros": [
    {
      "id": 1,
      "titulo": "Clean Code",
      "autor": "Robert C. Martin",
      "generoId": 3,
      "status": "lido",
      "avaliacao": 5,
      "favorito": true,
      "isbn": "9780132350884",
      "paginas": 464,
      "capaUrl": "https://covers.openlibrary.org/b/isbn/9780132350884-L.jpg",
      "dataInicio": "2026-01-05",
      "dataConclusao": "2026-01-30",
      "resenha": "Leitura obrigatória para todo desenvolvedor.",
      "criadoEm": "2026-01-05T09:00:00Z"
    },
    {
      "id": 2,
      "titulo": "O Hobbit",
      "autor": "J.R.R. Tolkien",
      "generoId": 1,
      "status": "lendo",
      "avaliacao": null,
      "favorito": false,
      "isbn": "9788533613422",
      "paginas": 336,
      "capaUrl": "https://covers.openlibrary.org/b/isbn/9788533613422-L.jpg",
      "dataInicio": "2026-03-01",
      "dataConclusao": null,
      "resenha": "",
      "criadoEm": "2026-03-01T08:00:00Z"
    }
  ],
  "generos": [
    { "id": 1, "nome": "Fantasia", "cor": "#8B5CF6" },
    { "id": 2, "nome": "Ficção Científica", "cor": "#3B82F6" },
    { "id": 3, "nome": "Tecnologia", "cor": "#10B981" },
    { "id": 4, "nome": "Romance", "cor": "#EC4899" },
    { "id": 5, "nome": "História", "cor": "#F59E0B" },
    { "id": 6, "nome": "Biografia", "cor": "#6B7280" },
    { "id": 7, "nome": "Terror", "cor": "#EF4444" },
    { "id": 8, "nome": "Autoajuda", "cor": "#F97316" }
  ]
}
```

---

## 2. Endpoints da API (JSON Server)

| Método | Endpoint | Descrição |
|--------|----------|-----------|
| GET | `/livros` | Lista todos os livros |
| GET | `/livros?status=lido` | Filtra por status |
| GET | `/livros?generoId=1` | Filtra por gênero |
| GET | `/livros/:id` | Busca livro por ID |
| POST | `/livros` | Cadastra novo livro |
| PUT | `/livros/:id` | Atualiza livro completo |
| PATCH | `/livros/:id` | Atualiza campos específicos |
| DELETE | `/livros/:id` | Remove livro |
| GET | `/generos` | Lista todos os gêneros |

---

## 3. APIs Públicas

### Open Library
- **Busca por ISBN:** `https://openlibrary.org/api/books?bibkeys=ISBN:{isbn}&format=json&jscmd=data`
- **Capa:** `https://covers.openlibrary.org/b/isbn/{isbn}-L.jpg`
- Documentação: https://openlibrary.org/developers/api

### ViaCEP
- **Busca por CEP:** `https://viacep.com.br/ws/{cep}/json/`
- Uso: autocompletar endereço no perfil do usuário
- Documentação: https://viacep.com.br

---

## 4. Validações (REGEX)

```javascript
// ISBN-10: 10 dígitos (último pode ser X)
const ISBN10 = /^[0-9]{9}[0-9X]$/;

// ISBN-13: 13 dígitos
const ISBN13 = /^[0-9]{13}$/;

// CEP: 8 dígitos
const CEP = /^[0-9]{8}$/;

// E-mail
const EMAIL = /^[^\s@]+@[^\s@]+\.[^\s@]+$/;

// Telefone: (XX) XXXXX-XXXX
const TELEFONE = /^\(\d{2}\)\s\d{4,5}-\d{4}$/;
```

---

## 5. localStorage

| Chave | Tipo | Descrição |
|-------|------|-----------|
| `gl_filtro_status` | string | Último filtro de status selecionado |
| `gl_filtro_genero` | string | Último filtro de gênero selecionado |
| `gl_tema` | string | Tema da UI (`light` \| `dark`) |
| `gl_perfil` | object | Dados do perfil do usuário |

---

## 6. Estrutura de Telas

### index.html — Dashboard
- Navbar responsiva
- Cards de estatísticas: Total, Lendo, Lidos, Meta Anual
- Carousel com livros recentes
- Seção de favoritos

### estante.html — Minha Estante
- Filtros por status (pills/tabs) e gênero (select)
- Grid de cards responsivo
- Cada card: capa, título, autor, badge de gênero, estrelas, botões editar/excluir
- Modal de confirmação de exclusão

### cadastro.html — Cadastro / Edição
- Campo ISBN com busca automática (Open Library)
- Formulário com validação completa
- Preview da capa ao buscar ISBN
- Select de gênero, radio de status, checkbox de favorito
- Campo de avaliação (1-5 estrelas clicável)

### perfil.html — Perfil do Usuário
- Formulário com nome, e-mail, telefone
- Campo CEP com preenchimento automático via ViaCEP

---

## 7. Tecnologias e Versões

| Tecnologia | Versão | CDN |
|-----------|--------|-----|
| Bootstrap | 5.3.3 | jsDelivr |
| jQuery | 3.7.1 | jsDelivr |
| jQuery Mask | 1.14.16 | jsDelivr |
| JSON Server | 1.0.0 | npm (local) |
| Sass | 1.77 | npm (local) |
| ESLint | 9.x | npm (local) |
| Prettier | 3.x | npm (local) |
