# Docker compose com Django e banco de dados

## Informações gerais

- Assunto: Docker, conteinizar aplicativos
- Disciplina: *sistemas operacionais*
- **Tarefa**:
  1. Criar um projeto django com uma aplicação web
    - alternativa, criar uma _branch_ no repositório do projeto integrador para configurar o acesso ao repositório de dados
  2. Criar um `Dockerfile` para o projeto django
  3. Criar a imagem e testar o conteiner para testar
  4. OPCIONAL, porque dependendo de como pergunta ao assistente de IA; criar um `Dockerfile` para o repositório de banco de dados
  5. Criar um `docker-compose.yml` e configurar para 2 serviços: `webapp` e `db`
  6. Configurar o arquivo django de acesso ao repositório de dados para usar o serviço docker `db`
  7. Testar o `docker-compose.yml`
  8. Relatar minimamente o que foi feito.
- **Entrega**: copia desse aquivo markdown preenchido, no seu repositório _fork_ de https://github.com/sistemas-operacionais/2024.2


## Relatório

### Aluno

- nome: Fabiana Campos Serra dos Santos
- matrícula: 20231014040033


## Relato

### 1. Criando o Projeto Django

Executamos os seguintes comandos para criar o projeto Django:

```bash
mkdir django-docker && cd django-docker
python -m venv venv
source venv/bin/activate # ou "venv\Scripts\activate" no Windows
pip install django
django-admin startproject myproject
```

Criamos a aplicação web alternativa:

```bash
python manage.py startapp webapp
```

### 2. Criando o Dockerfile para Django (Dockerfile)

```bash
# Usa a imagem oficial do Python
FROM python:3.9

# Define o diretório de trabalho dentro do container
WORKDIR /app

# Copia os arquivos para dentro do container
COPY requirements.txt requirements.txt
RUN pip install -r requirements.txt

COPY . .

# Expõe a porta do Django
EXPOSE 8000

# Comando para iniciar o servidor
CMD ["python", "manage.py", "runserver", "0.0.0
```

### Criando o docker-compose.yml

```bash
version: '3.8'

services:
  db:
    image: postgres:15
    container_name: db_container
    restart: always
    environment:
      POSTGRES_DB: mydatabase
      POSTGRES_USER: user
      POSTGRES_PASSWORD: password
    ports:
      - "5432:5432"
    volumes:
      - postgres_data:/var/lib/postgresql/data

  webapp:
    build: .
    container_name: django_app
    command: python manage.py runserver 0.0.0.0:8000
    volumes:
      - .:/app
    ports:
      - "8000:8000"
    depends_on:
      - db
    environment:
      - DATABASE_NAME=mydatabase
      - DATABASE_USER=user
      - DATABASE_PASSWORD=password
      - DATABASE_HOST=db
      - DATABASE_PORT=5432

volumes:
  postgres_data:
```

### Configuração do Django para o Banco de Dados (settings.py)
No arquivo settings.py, alteramos a configuração do banco de dados:

```bash
DATABASES = {
    'default': {
        'ENGINE': 'django.db.backends.postgresql',
        'NAME': os.getenv('DATABASE_NAME', 'mydatabase'),
        'USER': os.getenv('DATABASE_USER', 'user'),
        'PASSWORD': os.getenv('DATABASE_PASSWORD', 'password'),
        'HOST': os.getenv('DATABASE_HOST', 'db'),
        'PORT': os.getenv('DATABASE_PORT', '5432'),
    }
}
```

### Construção e Testes
Criamos a imagem e testamos o container com:

```bash
docker-compose up --build
```
Para verificar os logs:
```bash
docker-compose logs -f
```

### Conclusão
6. Conclusão

O projeto foi conteinerizado com sucesso usando Docker e Docker Compose. Agora, o Django pode interagir com um banco de dados PostgreSQL dentro do ambiente Dockerizado.
