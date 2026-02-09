# API ToDo Advogados

Sistema de gerenciamento de tarefas para advogados utilizarem no dia-a-dia! :D

## Configuração

Configure a variável `{{url}}` no seu ambiente apontando para a URL base da API.

## Endpoints

### Health

**GET** `/health`  
Verifica se a API está respondendo.

### Usuários

**POST** `/usuarios`  
Cria um novo usuário no sistema.

```json
{
  "nome": "string",
  "email": "string",
  "senha": "string"
}
```

**POST** `/login`  
Autentica um usuário e retorna o token de acesso.

```json
{
  "email": "string",
  "senha": "string"
}
```

O token retornado é armazenado automaticamente em `{{access_token}}`.

**GET** `/usuarios/me`  
Retorna os dados do usuário autenticado.  
Requer autenticação Bearer.

### Tarefas

Todos os endpoints de tarefas requerem autenticação Bearer com `{{access_token}}`.

**POST** `/tarefas`  
Cria uma nova tarefa.

```json
{
  "titulo": "string",
  "descricao": "string",
  "status": "pendente"
}
```

Status disponíveis: `pendente`, `em andamento`, `concluida`

**GET** `/tarefas`  
Lista todas as tarefas do usuário autenticado.

**GET** `/tarefas/:id`  
Retorna uma tarefa específica.

**PUT** `/tarefas/:id`  
Atualiza uma tarefa existente.

```json
{
  "titulo": "string",
  "descricao": "string"
}
```

**PUT** `/tarefas/:id` (status)  
Atualiza apenas o status de uma tarefa.

```json
{
  "status": "concluida"
}
```

**DELETE** `/tarefas/:id`  
Remove uma tarefa.

### Filtros por Status

**GET** `/tarefas?status=pendente`  
Lista tarefas pendentes.

**GET** `/tarefas?status=em andamento`  
Lista tarefas em andamento.

**GET** `/tarefas?status=concluida`  
Lista tarefas concluídas.

## Variáveis de Ambiente

- `url` - URL base da API
- `access_token` - Token JWT (gerado automaticamente no login)
- `user_id` - ID do usuário (gerado automaticamente no cadastro)
- `tarefa_id` - ID da tarefa (gerado automaticamente na criação)

## Autenticação

A API utiliza Bearer Token. Após fazer login, o token é automaticamente configurado nas requisições seguintes.

> Feito por Caio André! 😼
