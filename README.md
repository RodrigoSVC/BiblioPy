# BiblioPy

Sistema de Biblioteca desenvolvido em Python com FastAPI, demonstrando habilidades em desenvolvimento backend, arquitetura de software e boas práticas.

## Tecnologias

- **Backend:** FastAPI, SQLAlchemy, Pydantic
- **Banco de Dados:** SQLite
- **Validação:** Pydantic BaseModel
- **Documentação:** Swagger UI (automática)
- **Arquitetura:** SOLID Principles, Dependency Injection

## Funcionalidades Implementadas

### Modelos de Dados
- **Book:** Livros com título, autor, ISBN e status de disponibilidade
- **User:** Usuários com nome, email e telefone
- **Loan:** Empréstimos com relacionamentos entre usuários e livros
- **Category:** Categorias para organização dos livros

### Endpoints da API

#### Livros
- `POST /books` - Criar novo livro
- `GET /books` - Listar todos os livros
- `GET /books/{id}` - Buscar livro específico
- `PUT /books/{id}` - Atualizar livro
- `DELETE /books/{id}` - Deletar livro

#### Usuários
- `POST /users` - Criar novo usuário
- `GET /users` - Listar todos os usuários

#### Empréstimos
- `POST /loans` - Criar novo empréstimo

#### Categorias
- `POST /categories` - Criar nova categoria

#### Sistema
- `GET /` - Página inicial
- `GET /health` - Status da API
- `GET /docs` - Documentação Swagger UI

## Arquitetura

### Princípios SOLID Aplicados
- **Single Responsibility:** Cada modelo tem uma responsabilidade específica
- **Open/Closed:** Estrutura extensível para novos endpoints
- **Liskov Substitution:** Herança adequada nos modelos Pydantic
- **Interface Segregation:** Schemas específicos para entrada e saída
- **Dependency Inversion:** Injeção de dependência para conexões com banco

### Padrões Utilizados
- **Dependency Injection:** Gerenciamento automático de conexões com banco
- **Repository Pattern:** Separação entre lógica de negócio e acesso a dados
- **Data Transfer Objects (DTOs):** Modelos Pydantic para validação

## Como Executar

### Pré-requisitos
- Python 3.8+
- pip

### Instalação
```bash
# Clone o repositório
git clone https://github.com/RodrigoSVC/BiblioPy.git
cd BiblioPy

# Crie um ambiente virtual
python -m venv venv

# Ative o ambiente virtual (Windows)
venv\Scripts\activate

# Instale as dependências
pip install -r requirements.txt
```

### Execução
```bash
# Execute a aplicação
uvicorn app.main:app --reload
```

Acesse: http://localhost:8000

### Documentação da API
Acesse: http://localhost:8000/docs

## Estrutura do Projeto

```
biblioPy/
├── app/
│   ├── __init__.py
│   └── main.py          # Aplicação principal
├── static/
│   └── index.html       # Interface web
├── requirements.txt     # Dependências
├── .gitignore          # Arquivos ignorados
└── README.md           # Documentação
```

## Exemplos de Uso

### Criar um Livro
```bash
curl -X POST "http://localhost:8000/books" \
     -H "Content-Type: application/json" \
     -d '{"title":"O Senhor dos Anéis","author":"J.R.R. Tolkien","isbn":"9788533613379"}'
```

### Listar Livros
```bash
curl http://localhost:8000/books
```

### Buscar Livro Específico
```bash
curl http://localhost:8000/books/1
```

## Desenvolvimento

### Adicionando Novos Endpoints
1. Defina o modelo SQLAlchemy (se necessário)
2. Crie os schemas Pydantic (entrada e saída)
3. Implemente o endpoint com validação e tratamento de erros
4. Teste via Swagger UI

### Validação de Dados
Todos os dados de entrada são validados automaticamente pelo Pydantic, garantindo:
- Tipos corretos
- Campos obrigatórios
- Formato de dados adequado

### Tratamento de Erros
- 404: Recurso não encontrado
- 422: Dados inválidos
- 500: Erro interno do servidor

## Próximos Passos

- [ ] Implementar autenticação JWT
- [ ] Adicionar testes unitários
- [ ] Criar frontend completo
- [ ] Configurar Docker
- [ ] Deploy em produção
- [ ] Implementar cache Redis
- [ ] Adicionar logs estruturados
