
# Colégio Plural - API do Setor de Inclusão

API RESTful desenvolvida para automatizar e otimizar a gestão do Setor de Inclusão do Colégio Plural. O sistema substitui registros manuais por um controle digital seguro de alunos com necessidades específicas, seus respectivos responsáveis e o histórico dos atendimentos realizados.

## Sobre o Projeto

O Setor de Inclusão necessita de acompanhamento individualizado para alunos com necessidades especiais. Esta solução centraliza as informações cadastrais e de atendimento, eliminando duplicidade de registros e garantindo a segurança de dados sensíveis, conforme exigências de privacidade e controle de acesso.

## Funcionalidades Principais

- Autenticação e Segurança: Autenticação de usuários via Spring Security e JWT com tempo de expiração e criptografia de senhas.
- Gestão de Responsáveis: Cadastro, edição e busca paginada por termo (nome ou CPF).
- Gestão de Alunos: Cadastro de alunos associados obrigatoriamente a um responsável legal.
- Gestão de Atendimentos:
  - Registro de atendimentos vinculados a alunos e profissionais.
  - Listagem de atendimentos ordenada por data, incluindo dados do aluno e do responsável.
  - Atualização da data e horário de atendimentos agendados.

## Tecnologias Utilizadas

- Linguagem: Java 17+
- Framework: Spring Boot 3
  - Spring Data JPA (Persistência de dados)
  - Spring Security (Autenticação e autorização)
  - Bean Validation (Validação de dados de entrada)
- Banco de Dados: PostgreSQL
- Documentação da API: OpenAPI / Swagger UI
- Gerenciador de Dependências: Maven

## Estrutura do Banco de Dados

O banco de dados relacional é composto pelas seguintes entidades principais:

- usuarios: Profissionais do setor de inclusão (login e senha criptografada).
- responsaveis: Dados dos pais ou tutores legais.
- alunos: Crianças acompanhadas pelo setor (vinculadas a um responsável).
- atendimentos: Histórico de acompanhamentos (vinculados a um aluno e a um usuário).

## Endpoints Principais da API

### Autenticação
- POST /api/auth/login - Autenticação do usuário e geração de token JWT.

### Responsáveis
- GET /api/responsaveis?termo={busca} - Lista e busca responsáveis por nome ou CPF.
- POST /api/responsaveis - Cadastra um novo responsável.
- GET /api/responsaveis/{id} - Obtém detalhes de um responsável.

### Alunos
- POST /api/alunos - Cadastra um novo aluno associado a um responsável existente.
- GET /api/alunos - Lista alunos cadastrados.

### Atendimentos
- GET /api/atendimentos - Lista atendimentos ordenados por data.
- POST /api/atendimentos - Registra um novo atendimento.
- PATCH /api/atendimentos/{id}/data - Atualiza a data de um atendimento existente.
