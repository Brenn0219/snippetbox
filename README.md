# Snippetbox

O Snippetbox é um aplicativo web que desenvolvi em Go, inspirado no livro "Let's Go" de Alex Edwards. Meu objetivo com este projeto foi criar uma ferramenta de aprendizado para construção de aplicações web em Go, aplicando práticas recomendadas e técnicas modernas.

## Introdução

O Snippetbox permite que os usuários colem e compartilhem trechos de texto, de forma semelhante ao Pastebin ou GitHub Gists. Comecei o projeto de forma incremental, partindo de uma página web simples e evoluindo para uma aplicação completa, onde os usuários podem salvar e visualizar snippets. Ao longo do desenvolvimento, abordei tópicos essenciais para o desenvolvimento web, como estruturação de projetos, roteamento de solicitações, integração com bancos de dados, processamento de formulários e exibição segura de dados dinâmicos.

## Funcionalidades

1. **Criação e Visualização de Snippets**:
   - Usuários podem criar snippets de texto e visualizá-los através da aplicação.

2. **Gerenciamento de Usuários**:
   - Implementação de contas de usuário, onde apenas usuários registrados podem criar snippets.

3. **Segurança**:
   - Configuração de um servidor HTTPS.
   - Gerenciamento de sessões e autenticação de usuário.

4. **Roteamento e Manipulação de Solicitações HTTP**:
   - Encaminhamento de solicitações para manipuladores específicos baseados no caminho da solicitação.
   - Envio de diferentes respostas HTTP, cabeçalhos e códigos de status.

5. **Validação e Processamento de Entradas**:
   - Validação de entradas de usuários a partir de parâmetros de string de consulta de URL.

6. **Estrutura de Projeto**:
   - Organização sensata e escalável do projeto.

7. **Renderização de Páginas HTML**:
   - Utilização de herança de modelo para manter a marcação livre de código duplicado.
   - Servir arquivos estáticos como imagens, CSS e JavaScript.

## Instalação

1. Clone o repositório para sua máquina local:
   ```sh
   git clone https://github.com/seu-usuario/snippetbox.git
   ```
2. Navegue até o diretório do projeto:
   ```sh
   cd snippetbox
   ```
3. Instale as dependências:
   ```sh
   go mod tidy
   ```
4. Configure o banco de dados MySQL:
   ```sh
   CREATE DATABASE snippetbox CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci;

   USE snippetbox;

   CREATE TABLE snippets (
      id INTEGER NOT NULL PRIMARY KEY AUTO_INCREMENT,
      title VARCHAR(100) NOT NULL,
      content TEXT NOT NULL,
      created DATETIME NOT NULL,
      expires DATETIME NOT NULL
   );

   CREATE INDEX idx_snippets_created ON snippets(created);

   CREATE USER 'web'@'localhost';
   GRANT SELECT, INSERT, UPDATE, DELETE ON snippetbox.* TO 'web'@'localhost';
   ALTER USER 'web'@'localhost' IDENTIFIED BY 'snippetbox';
   ```
5. Para inserir alguns snippets de exemplo:
   ```sh
   INSERT INTO snippets (title, content, created, expires) VALUES (
    'An old silent pond',
    'An old silent pond...\nA frog jumps into the pond,\nsplash! Silence again.\n\n– Matsuo Bashō',
    UTC_TIMESTAMP(),
    DATE_ADD(UTC_TIMESTAMP(), INTERVAL 365 DAY)
   );

   INSERT INTO snippets (title, content, created, expires) VALUES (
      'Over the wintry forest',
      'Over the wintry\nforest, winds howl in rage\nwith no leaves to blow.\n\n– Natsume Soseki',
      UTC_TIMESTAMP(),
      DATE_ADD(UTC_TIMESTAMP(), INTERVAL 365 DAY)
   );

   INSERT INTO snippets (title, content, created, expires) VALUES (
      'First autumn morning',
      'First autumn morning\nthe mirror I stare into\nshows my father''s face.\n\n– Murakami Kijo',
      UTC_TIMESTAMP(),
      DATE_ADD(UTC_TIMESTAMP(), INTERVAL 7 DAY)
   );
   ```
6. Crie a tabela de sessões para o gerenciamento de usuários:
   ```sh
   USE snippetbox;

   CREATE TABLE sessions (
      token CHAR(43) PRIMARY KEY,
      data BLOB NOT NULL,
      expiry TIMESTAMP(6) NOT NULL
   );

   CREATE INDEX sessions_expiry_idx ON sessions (expiry);
   ```

7. Crie a tabela de usuários para cadastrar novos usuários:
   ```sh
   CREATE TABLE users (
   id INTEGER NOT NULL PRIMARY KEY AUTO_INCREMENT,
   name VARCHAR(255) NOT NULL,
   email VARCHAR(255) NOT NULL,
   hashed_password CHAR(60) NOT NULL,
   created DATETIME NOT NULL
   );

   ALTER TABLE users ADD CONSTRAINT users_uc_email UNIQUE (email);
   ```

8. Inicie o servidor:
   ```sh
   go run cmd/web/*
   ```

## Tecnologias Usadas
* Go
* HTML/CSS
* JavaScript
* MySQL
* Curl

## Recursos

- [Livro "Let's Go" de Alex Edwards](https://lets-go.alexedwards.net/)

## Licença

Este projeto está licenciado sob a [MIT License](LICENSE).