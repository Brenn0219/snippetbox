# Snippetbox

Snippetbox é um aplicativo web desenvolvido em Go, inspirado no livro "Let's Go" de Alex Edwards. Este projeto tem como objetivo ser uma ferramenta de aprendizado para construção de aplicações web em Go, guiando os desenvolvedores através de práticas recomendadas e técnicas modernas.

## Introdução

Snippetbox permite que os usuários colem e compartilhem trechos de texto, similar ao Pastebin ou GitHub Gists. O projeto é desenvolvido incrementalmente, começando de uma página web simples e evoluindo para uma aplicação completa onde os usuários podem salvar e visualizar snippets. O projeto cobre tópicos essenciais para o desenvolvimento web, como estruturação de projetos, roteamento de solicitações, integração com bancos de dados, processamento de formulários e exibição segura de dados dinâmicos.

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
4. Inicie o servidor:
   ```sh
   go run cmd/web/*
   ```

## Recursos

- [Livro "Let's Go" de Alex Edwards](https://lets-go.alexedwards.net/)

## Licença

Este projeto está licenciado sob a [MIT License](LICENSE).