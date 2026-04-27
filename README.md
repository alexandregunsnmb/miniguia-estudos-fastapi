# 📗  miniguia-estudos-fastapi
Miniguia estudos do framawork Fastapi com uso do notebooklm para aprender os conseitos basicos ao avançado com o objetivo de implementar um projeto em python em FastApi.
Ententer os conceitos de escalabilidade em um projeto FastAPI, estrutura e divisão de pastas e como aplicar a seguraça em um projeto.


### Curadoria de Fontes:
#### FONTES DE VÍDEO:
> https://www.youtube.com/watch?v=SORiTsvnU28
> https://www.youtube.com/watch?v=-eIWgi35Q8s&t=137s
> https://www.youtube.com/watch?v=Af6Zr0tNNdE
> https://www.youtube.com/watch?v=f270BoTicMA
> https://www.youtube.com/watch?v=H9Blu0kWdZE&list=PLK8U0kF0E_D6l19LhOGWhVZ3sQ6ujJKq_
> https://www.youtube.com/watch?v=0zb2kohYZIM&list=PLK8U0kF0E_D6l19LhOGWhVZ3sQ6ujJKq_&index=7
> https://www.youtube.com/watch?v=92iCfXAK0Gc&list=PLK8U0kF0E_D6l19LhOGWhVZ3sQ6ujJKq_&index=11
> https://www.youtube.com/watch?v=YpvcqxYiyNE&list=PLK8U0kF0E_D6l19LhOGWhVZ3sQ6ujJKq_&index=22

#### FONTES DE TEXTO:
> https://fastapi.tiangolo.com/

> https://fastapidozero.dunossauro.com/estavel/

### Engenharia de Prompts: 

PROMPT 01:
Converse sobre o que essas fontes dizem de Estrutura de Pastas, no contexto mais amplo de Anatomia de um Projeto Escalável em FastAPI.

PROMPT 02:
Quais são as principais vantagens do FastAPI em relação ao Django e Flask?

PROMPT 03:
Métodos Sync e Async
Mostre:
- qual é diferença do Sycn com o Async na implementação de métodos;
- Quando e quais casos deve ser aplicado;
- Qual diferença de performace;
- Como deve ser implementado em um projeto de Backend;
- Exemplo aplicado em uma estrutura de camadas MVC;
- O que munda para o banco de dados Postgres.

PROMPT 04:
Qual a diferença entre o driver síncrono e o asyncpg?

PROMPT 05:
Quais bibliotescas usadas para um projeto MVC?

PROMPT 06:
Apresente uma estrutura de pastas de um projeto backend em FastApi

PROMPT 07:
Como funciona a injeção de dependência no FastAPI?

PROMPT 08:
Como funcionam as Background Tasks para envio de e-mails?

PROMPT 09:
Como funcionam as Background Tasks para envio de e-mails?

PROMPT 10:
Qual a finalidade do Pydantic e como aplica-lo?

### Resumo:
Os tópicos discutidos até agora sobre o FastAPI e o desenvolvimento de backend escalável resumem-se em cinco eixos principais:

Vantagens do FastAPI em relação a Django e Flask: 
- Destacamos que o FastAPI oferece um desempenho excepcionalmente superior, processando até quase três vezes mais requisições por segundo que o Django em testes de operações CRUD, graças à sua arquitetura moderna e suporte nativo a operações assíncronas. 

- Ele também brilha pela validação de dados embutida (via Pydantic) e pela geração automática de documentação interativa baseada nos padrões OpenAPI.
Anatomia e Estrutura de Pastas Escalável: Exploramos a importância do baixo acoplamento para o crescimento do sistema. 

Apresentamos duas formas de organização: 
- Arquitetura Limpa/Domínios (que separa pacotes por regras de negócio, como users/ e auth/ com seus próprios controladores, serviços e modelos) e a Separação por Camadas Técnicas (que divide o projeto em pastas como api/, services/, models/ e database/). Em ambas, destacou-se a separação estrita da pasta de testes. 

Paradigma Síncrono vs. Assíncrono: 
- Usando a analogia do Bob Esponja preparando hambúrgueres, detalhamos como métodos assíncronos (async/await) otimizam agressivamente o tempo ocioso do servidor durante operações de rede e disco (I/O Bound), ao contrário do modelo síncrono que bloqueia a execução. Também abordamos como o uso de drivers de banco de dados nativamente assíncronos (como o asyncpg) extrai o máximo de performance nessa arquitetura.

### Principais conceitos aprendidos;
- Arquitetura Limpa (Clean Architecture): Padrão de design estrutural que organiza o código para facilitar a manutenção e escalabilidade.
- Controllers/Rotas HTTP (api/): Camada fina responsável apenas por receber e devolver requisições
- Assíncrono (Async): O programa otimiza ativamente os tempos de espera
- Síncrono (Sync): O código viaja em linha reta
- Event Loop (Laço de Eventos): Orquestra e distribui as tarefas assíncronas
- Injeção de Dependências (Dependency Injection - DI): Um padrão focado na Inversão de Controle
- Pydantic: A biblioteca central do FastAPI responsável pela validação automática de dados e serialização
- ORMs (SQLAlchemy e SQLModel): Bibliotecas de Mapeamento Objeto-Relacional
- Alembic: Ferramenta do ecossistema SQLAlchemy utilizada para gerenciar as migrações do projeto
- Uvicorn: Servidor web assíncrono ASGI encarregado de rodar a aplicação
- TestClient (pytest e httpx) Mecanismo de qualidade e testes de software
- Tasks (e TaskGroup): Ferramentas usadas para agendar e rodar múltiplas corrotinas concorrentemente o mais rápido possível

## 📦 Dependencies de um projeto backend

### FastAPI

Dependencies for fastapi:

- Python
- uvicorn (Servidor Local para rodar projeto)
- fastapi (Requisições HTTP - Routs)

---

### Database (PostgreSQL)

Dependencies for database postgresql:

- SQLAlchemy (ORM para trabalhar com banco de dados relacionais)
- sqlmodel
- asyncpg
- psycopg2 (feramenta para conectar com Postgres)

---

### Schema / Data Validation

Dependencies for schema data wrapper:

- pydantic (validação de entrada → converter JSON → objetos Python)
- alembic (migrations de tabelas do banco de dados para criar e modificar)

---

### Security

- passlib[bcrypt] (para savar criptografado a senha do usuario no banco de dados)
- python-jose[cryptography] Gerar Token

## 📦Aplicação e Uso

Esta seção descreve **cada dependência do projeto**, sua finalidade e **como ela é usada dentro de uma arquitetura backend com FastAPI**.

---

## Framework

### 🚀 fastapi

Framework moderno para criação de **APIs REST em Python**.

Principais usos:

- criação de endpoints HTTP
- validação automática de dados
- integração com Pydantic
- geração automática de documentação (Swagger / OpenAPI)

Exemplo:

```python
from fastapi import FastAPI

app = FastAPI()

@app.get("/users")
def list_users():
    return {"users": []}
```

### 🌍 uvicorn

#### Servidor ASGI responsável por executar a aplicação FastAPI.

Função:

- rodar a aplicação
- lidar com requisições HTTP
- permitir alta performance assíncrona

Exemplo de execução:
```Bach
uvicorn app.main:app --reload
```

## 🗄️ Banco de Dados

### SQLAlchemy

ORM (Object Relational Mapper) usado para mapear objetos Python para tabelas do banco.

Funções:

- criar modelos de dados
- executar consultas
- gerenciar sessões do banco

Exemplo:
```python
class User(Base):
    __tablename__ = "users"

    id = Column(UUID, primary_key=True)
    email = Column(String)
```

###  sqlmodel

Biblioteca que combina:

- SQLAlchemy
- Pydantic

Permite definir modelos que funcionam como ORM e schema ao mesmo tempo.

Exemplo:
```python
from sqlmodel import SQLModel, Field

class User(SQLModel, table=True):
    id: int | None = Field(default=None, primary_key=True)
    email: str
```

### asyncpg

Driver assíncrono de conexão com PostgreSQL.

Benefícios:

- maior performance
- suporte a operações async
- ideal para aplicações FastAPI

Exemplo de uso:
```python
postgresql+asyncpg://user:password@localhost/db
```

###  psycopg2

Driver tradicional síncrono para PostgreSQL.

Usado quando:

- não se utiliza async
- integração com ferramentas como Alembic

### 🔎 Validação de Dados
#### pydantic

Biblioteca para validação e serialização de dados.

Usada em:

- schemas de entrada da API
- validação automática
- conversão JSON → objetos Python

Exemplo:
```python
from pydantic import BaseModel

class UserCreate(BaseModel):
    email: str
    password: str
```

## 🗃️ Migração de Banco
#### alembic

Ferramenta para versionamento do banco de dados.

Permite:

- criar migrations
- atualizar schema do banco
- manter histórico das alterações

Exemplo de comandos:
```python
alembic revision --autogenerate -m "create users table"
alembic upgrade head
```

### 🔐 Segurança
#### passlib[bcrypt]

Biblioteca usada para hash de senhas.

Utiliza algoritmo bcrypt, considerado seguro para armazenamento de senhas.

Exemplo:
```python
from passlib.context import CryptContext

pwd_context = CryptContext(schemes=["bcrypt"])

hashed_password = pwd_context.hash("minha_senha")
```

#### python-jose[cryptography]

Biblioteca para criação e validação de tokens JWT.

Usada para:

- autenticação
- autorização
- sessões stateless

Exemplo:
```python
from jose import jwt

token = jwt.encode(
    {"user_id": "123"},
    "SECRET_KEY",
    algorithm="HS256"
)
```

### 🧠 Como essas dependências trabalham juntas

Fluxo típico da aplicação:
```
Client Request
      ↓
FastAPI
      ↓
Pydantic (validação)
      ↓
Service (lógica)
      ↓
SQLAlchemy / SQLModel
      ↓
PostgreSQL (asyncpg / psycopg2)
```
Autenticação:
```
User Login
    ↓
Passlib → valida senha
    ↓
python-jose → gera JWT
    ↓
FastAPI retorna token
```
### 📊 Resumo

| Dependência     | Função                  |
| --------------- | ----------------------- |
| fastapi         | Framework da API        |
| uvicorn         | Servidor ASGI           |
| SQLAlchemy      | ORM para banco          |
| sqlmodel        | ORM + validação         |
| asyncpg         | Driver async PostgreSQL |
| psycopg2        | Driver sync PostgreSQL  |
| pydantic        | Validação de dados      |
| alembic         | Migração de banco       |
| passlib[bcrypt] | Hash de senha           |
| python-jose     | Autenticação JWT        |

