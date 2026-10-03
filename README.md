# API de Gestão de Vendas

**Aluno:** Vinicius Schaefer Vieira  
**Unidade curricular:** Desenvolvimento de APIs — SENAI  
**Tecnologias:** Node.js, Express, MySQL e mysql2

## Recursos implementados
- `/clientes`: CRUD básico de clientes.
- `/produtos`: CRUD de produtos, com paginação em `GET /produtos?page=1&limit=20`.
- `/usuarios`: CRUD completo, incluindo atualização parcial com `PATCH`.
- `/pedidos`: criação e consulta de pedidos, alteração de status e gerenciamento dos itens.

## Requisitos
- Node.js 18 ou superior
- MySQL 8 (ou versão compatível)
- npm
- Postman ou Insomnia (opcional, para executar a coleção)

## Instalação
1. Crie o banco e as tabelas executando `sql/script_banco.sql` no MySQL.
2. Copie `.env.example` para `.env` e ajuste as credenciais do seu banco.
3. No terminal, na raiz do projeto, execute:
   ```bash
   npm install
   npm run dev
   ```
4. A API ficará disponível em `http://localhost:3000`.

## Variáveis de ambiente
Configure `PORT`, `DB_HOST`, `DB_PORT`, `DB_USER`, `DB_PASSWORD` e `DB_NAME`.
Não compartilhe o arquivo `.env` nem publique senhas no Git.

## Rotas principais

| Método | Rota | Função |
|---|---|---|
| POST | `/clientes` | Cadastrar cliente |
| GET | `/clientes` | Listar clientes |
| GET | `/clientes/:id` | Buscar cliente |
| PUT | `/clientes/:id` | Atualizar cliente |
| DELETE | `/clientes/:id` | Remover cliente |
| POST | `/produtos` | Cadastrar produto |
| GET | `/produtos` | Listar produtos paginados |
| GET | `/produtos/:id` | Buscar produto |
| PUT | `/produtos/:id` | Atualizar produto |
| DELETE | `/produtos/:id` | Remover produto |
| POST | `/usuarios` | Cadastrar usuário |
| GET | `/usuarios` | Listar usuários |
| GET | `/usuarios/:id` | Buscar usuário |
| PUT | `/usuarios/:id` | Atualizar usuário por completo |
| PATCH | `/usuarios/:id` | Atualizar campos selecionados |
| DELETE | `/usuarios/:id` | Remover usuário |
| POST | `/pedidos` | Criar pedido associado a cliente |
| GET | `/pedidos` | Listar pedidos e cliente |
| GET | `/pedidos/:id` | Pedido, cliente e itens |
| PATCH | `/pedidos/:id/status` | Alterar status do pedido |
| POST | `/pedidos/:id/itens` | Adicionar item ao pedido |
| DELETE | `/pedidos/:id_pedido/itens/:id_item` | Remover item do pedido |

## Códigos HTTP usados
- `200 OK`: consulta ou atualização concluída.
- `201 Created`: recurso criado.
- `204 No Content`: exclusão concluída.
- `400 Bad Request`: dados inválidos ou obrigatórios ausentes.
- `404 Not Found`: recurso não encontrado.
- `409 Conflict`: e-mail duplicado ou restrição de integridade.
- `500 Internal Server Error`: erro inesperado no servidor.

## Testes HTTP
Importe `postman/colecao_api_gestao_vendas.json` no Postman. A coleção inclui exemplos de chamadas para os endpoints; ajuste IDs e execute as requisições na ordem apropriada. A coleção é um roteiro de testes, não comprova que testes foram executados.

## Observações importantes antes de entregar
- A senha de usuário está armazenada diretamente neste protótipo para manter as dependências alinhadas ao roteiro. **Não use em produção sem implementar hash com bcrypt/Argon2 e autenticação/autorização.**
- O requisito do enunciado que limita exclusão a administradores ainda precisa de autenticação e middleware de autorização. O campo `perfil` existe, mas não representa proteção de rota sozinho.
- Execute os testes com o seu banco local e revise os resultados no Postman/Insomnia antes de afirmar que todos passaram.
- O código foi preparado como base de projeto completa, mas precisa ser instalado e validado no ambiente do aluno.
