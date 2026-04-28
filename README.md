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


1. O Fluxo no Terminal
usou o Artisan, que é a interface de linha de comando do Laravel.

composer create-project: baixou o esqueleto do framework.

php artisan make:model Post -mcr: Esse comando é um "combo". Em vez de criar 3 arquivos separados, ele criou:

Model (-m): A representação da sua tabela no código.

Migration (-c): O arquivo que diz ao banco de dados como criar a tabela.

Controller (-r): O arquivo com os métodos (CRUD) para processar os dados.

2. O Mapa das Pastas
O Laravel segue o padrão Convention over Configuration (Convenção sobre Configuração). Isso significa que cada coisa tem seu lugar obrigatório:

📂 app/Models
Aqui fica o arquivo Post.php.

O que faz: É a ponte entre o PHP e o Banco de Dados. Quando você faz Post::all(), o Laravel traduz isso para SELECT * FROM posts automaticamente.

O que você fez: Adicionou o $fillable, que é uma trava de segurança para dizer quais campos podem ser preenchidos pelo usuário.

📂 app/Http/Controllers
Aqui fica o PostController.php.

O que faz: É o "cérebro". Ele recebe a requisição do usuário, valida se os dados são reais, manda o Model salvar e decide para qual página o usuário vai depois.

O que você fez: Criou a lógica no método store para validar os dados antes de salvar.

📂 database/migrations
Aqui ficam os arquivos de "blueprint" do banco.

O que faz: Em vez de você abrir o MySQL e criar colunas na mão, você escreve aqui. Isso permite que qualquer colega de equipe rode o projeto com a mesma estrutura de banco que a sua.

O que você fez: Definiu que um post tem title (string) e content (text).

📂 routes
O arquivo web.php.

O que faz: É o "telefonista". Se alguém acessa /posts, ele sabe que deve chamar o PostController.

O que você fez: Usou o Route::resource, que cria automaticamente 7 rotas padrão (listar, criar, editar, deletar, etc).

3. O Ciclo de Vida de um Dado
Imagine que um usuário clica em "Salvar Post" no seu blog. O que acontece?

Rota (routes/web.php): Identifica que é um envio de formulário para /posts.

Controller (store): Recebe os dados.

Validação: O código que escrevemos verifica: "O título está vazio? Já existe no banco?". Se estiver errado, o Laravel para tudo e avisa o usuário.

Model (Post::create): Se estiver tudo certo, o Model "conversa" com o banco e insere a linha.

Redirecionamento: O Controller manda o usuário de volta para a lista de posts com uma mensagem de sucesso.
