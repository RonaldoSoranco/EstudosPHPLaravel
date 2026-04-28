 Laravel Blog Core 

Este projeto é um sistema de blog minimalista desenvolvido para consolidar conhecimentos fundamentais em **PHP 8** e no framework **Laravel**. O foco principal foi a transição de conceitos de outras linguagens (como Java/Spring Boot) para o ecossistema PHP moderno.

O que eu estudei neste projeto

Durante o desenvolvimento, foquei em dominar os pilares do Laravel que garantem produtividade e segurança:

- **Arquitetura MVC:** Separação clara de responsabilidades entre Model, View e Controller.
- **Eloquent ORM:** Manipulação de banco de dados de forma expressiva e segura (Active Record).
- **Database Migrations:** Versionamento de banco de dados, garantindo que a estrutura da aplicação seja replicável.
- **Validação de Dados:** Implementação de regras de segurança no backend para garantir a integridade das informações.
- **Blade Engine:** Utilização do motor de templates do Laravel para renderização dinâmica de conteúdo.
- **Artisan CLI:** Automação de tarefas via linha de comando (criação de controllers, models e execução de migrações).

Passo a Passo do Desenvolvimento

1.  **Configuração do Ambiente:** Inicialização do projeto via Composer e configuração do ambiente Linux (Pop!_OS/Mint).
2.  **Estruturação de Dados:** Criação da Migration para a tabela de `posts` com campos de título e conteúdo.
3.  **Desenvolvimento do Model:** Configuração de `fillable` no Model `Post` para proteção contra *Mass Assignment*.
4.  **Lógica de Negócio (Controller):** Implementação de um *Resource Controller* para gerenciar as rotas de forma padronizada.
5.  **Camada de Segurança:** Adição de validação robusta no método `store`, garantindo campos obrigatórios e títulos únicos.
6.  **Persistência:** Integração total com banco de dados via Eloquent para criação e listagem de posts.
