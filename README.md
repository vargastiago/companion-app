# Companion App

Projeto básico que simula uma rede social.

Este projeto é baseado no conteúdo do livro "Vue.js 3 for Beginners", com o objetivo de aprender o framework Vue.js.

## Demo

Acesse o projeto em: https://vargastiago.github.io/companion-app

## Log de Funcionalidades

### Implementadas

- Estrutura SPA com Vue Router, incluindo rotas Home e About.
- Feed social com listagem de posts via API (DummyJSON).
- Enriquecimento dos posts com dados de usuário (nome e avatar).
- Exibição de curtidas por post.
- Exibiço de comentários por post com carregamento dinâmico.
- Exclusão de post no feed (remocao local da lista).
- Componentização da interface (header, sidebar, botão, ícones, post e comentários).
- Pipeline de deploy para GitHub Pages via GitHub Actions.
- Base de qualidade configurada com ESLint, Prettier, Vitest e Cypress.

### Incompletas / Em desenvolvimento

- Criação de post ainda sem lógica funcional (formulário sem persistência/integração no feed).
- Botão de criação na sidebar sem ação conectada.
- Estado de seleção visual do post incompleto/inconsistente.
- Testes automatizados não implementados.
- Store Pinia de exemplo ainda não integrada ao fluxo principal.
- Página About ainda com conteúdo básico/placeholder.
- Fluxos de API sem tratamento robusto de loading, erro e retry.
