```markdown
# Bantads - Internet Banking

Este projeto é o desenvolvimento de um sistema de Internet Banking para o banco fictício **BANTADS**, implementado utilizando Angular e Java Spring em uma arquitetura de microsserviços. A solução tem como foco atender três perfis de usuários: **Clientes**, **Gerentes** e **Administradores**, com funcionalidades específicas para cada perfil.

## Arquitetura e Tecnologias

O sistema foi projetado com base nos seguintes conceitos e tecnologias:

- **Arquitetura de Microsserviços**: cada serviço é independente, com seu próprio banco de dados.
- **API Gateway**: para expor as APIs.
- **Database per Service**: cada microsserviço possui seu próprio banco de dados PostgreSQL.
- **CQRS**: utilizado no microsserviço de Conta, para consultas separadas de comandos.
- **SAGA Orquestrada**: para garantir a consistência de transações entre serviços via RabbitMQ.
- **Docker**: todos os serviços são executados em contêineres separados.
- **Angular 14**: usado para o front-end.
- **Spring Boot (Java/Kotlin)**: utilizado para a implementação dos microsserviços.
- **PostgreSQL**: banco de dados relacional.
- **RabbitMQ**: utilizado para mensageria assíncrona entre os serviços.

## Funcionalidades por Perfil

### Cliente
- **Autocadastro**: Clientes podem se cadastrar sem a necessidade de login, com criação automática de uma conta pendente de aprovação.
- **Login/Logout**: Acesso ao sistema através de email e senha.
- **Tela Inicial**: Exibe saldo atual, operações disponíveis e histórico de transações.
- **Depósito e Saque**: Simulação de depósito e saque de valores.
- **Transferência**: Transferência de valores entre contas do banco.
- **Consulta de Saldo e Extrato**: Clientes podem consultar seu saldo e extrato de movimentações.

### Gerente
- **Aprovação de Contas**: Gerentes recebem pedidos de autocadastro para aprovação ou reprovação.
- **Consulta de Clientes**: Visualização de uma lista de clientes com opção de busca.
- **Consulta dos Melhores Clientes**: Visualização dos cinco clientes com maiores saldos.

### Administrador
- **Gerenciamento de Gerentes**: CRUD de gerentes, permitindo o controle total sobre os dados desses usuários.
- **Dashboard de Gerentes**: Visualização de informações agregadas sobre os gerentes, incluindo número de clientes e saldos totais.

## Como Executar

1. Clone o repositório:
   ```bash
   git clone https://github.com/seu-repositorio/bantads.git
   ```
2. Navegue até a pasta do projeto:
   ```bash
   cd bantads
   ```
3. Para iniciar todos os serviços usando Docker:
   ```bash
   docker-compose up
   ```

4. Para executar o script de automação, utilize:
   ```bash
   bash up_modern.sh
   ```

Este script permite a seleção de qual serviço deseja iniciar a partir de uma interface de menu interativa.

## Testes

- O projeto inclui testes automatizados para o front-end e back-end. Para rodar os testes no front-end, utilize:
   ```bash
   npm run test
   ```

## Postman Collection

Há uma coleção Postman disponível para testar as APIs dos microsserviços. As principais requisições estão listadas na coleção `Bantads.postman_collection.json`.

Exemplo de requisições:

- **Autocadastro**: POST `localhost:3000/api/v1/autocadastro`
- **Login**: POST `localhost:3000/api/v1/logar`
- **Consulta de Contas Pendentes**: GET `localhost:3000/api/v1/contas/pendentes`

## Requisitos Funcionais

Conforme descrito no [enunciado do projeto](enunciado.pdf), o sistema implementa os seguintes requisitos principais para cada perfil de usuário, incluindo funcionalidades de cadastro, transações, consultas e gerenciamento.

## Licença

Este projeto é de código aberto sob a licença MIT. Consulte o arquivo [LICENSE](LICENSE) para obter mais informações.
```
