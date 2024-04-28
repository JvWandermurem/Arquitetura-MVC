# Arquitetura-MVC
 Atividade Ponderada realizada para o desenvolvimento do WAD e da aplicação WEB referente o móduoo 2 do Instituto de tecnologia e liderança.


#  Phoenix Web

O projeto consiste em uma plataforma de acompanhamento dos grupos do desafio CESIM, que mostra uma visualização de dados sobre cada membro do grupo e do grupo como um todo. A plataforma é responsável por registrar avaliações e perfilamentos para os universitários de diferentes países participantes do desafio, com o objetivo de melhorar a relação entre os membros de um grupo.

## Arquitetura:

<div align="center">
<sub>MVC (Model-View-Controller)</sub>
<br>
<br>
<img src="/MVC Ponderada.jpeg" width="100%">
</div>

## Ferramenta de Diagramação:
- draw.io

## Modelos (Models):
- **Informações Pessoais**:
  - **Atributos**: ID, Foto, Bio, Senha, Email, Características.
  - **Utilização**: Armazena dados do usuário para autenticação e perfil.
- **Formulário/Avaliação**:
  - **Atributos**: Avaliação de Grupo, Avaliação Individual, Avaliação em Pares.
  - **Utilização**: Registra as respostas das avaliações aplicadas aos usuários.
- **Reportes**:
  - **Atributos**: Reportes
  - **Utilização**: Registra os reportes dos membros do grupo e pessoais.
- **Relações**:
  - Usuários e Avaliações: Os usuários recebem e preenchem avaliações, criando um vínculo direto entre estas entidades.

## Controladores (Controllers):
- **Informações Coletadas**:
  - **Ações**: Salva, Atualiza.
  - **Dados**: Recebe dados de avaliações individuais e informações pessoais tais como senha, email, foto, Bio e reportes dos usuários para serem armazenados ou atualizados no model.
- **Usuários**:
  - **Ações**: Busca, Lista, Atualiza.
  - **Dados**: Interage com o modelo de informações do grupo e algumas pessoais para gerenciar os dados dos usuários atualizando, buscando e listando essas informações.

## Views (Views):
- **Login**: Dá o acesso ao site para o usuário;
- **1º Formulário**: O primeiro formulário que o usuário responde ao entrar no site;
- **Homepage**: Local onde as informações principais sobre os membros do grupo estão;
- **Página de Avaliação**: Página para que os membros possam se avaliar e avaliar o grupo quando a avaliação estiver disponível.
- **Perfil**: Local onde o usuário pode alterar suas informações pessoais
- **Página de reporte**: Local para os usuários colocarem seus reportes e informações úteis ao projeto
- **Header**: Barra superior onde dá acesso às outras páginas

## Infraestrutura:
- **Componentes**:
  - **Dbreave**: Ferramenta de modelagem de dados para desenhar diagramas de entidade-relacionamento, importante para visualizar a estrutura do banco de dados. Garante que a base de dados seja organizada e fácil de entender.
  - **PostgreSQL**: É um sistema de gerenciamento de banco de dados objeto-relacional avançado ele oferece escalabilidade e integridade de dados, que são cruciais para o projeto envolvendo dados de avaliações de usuários internacionais.
  - **Sails.js**: Framework que facilita o desenvolvimento de aplicações web em Node.js seguindo o padrão MVC, incluindo funcionalidades de ORM (Object-relational mapping) com Waterline, facilitando a interação com o PostgreSQL.
  - **Node.js**: É um ambiente de execução JavaScript no lado do servidor que é leve, eficiente e ideal para construir aplicações web escaláveis. Permite o manejo de múltiplas conexões simultâneas com uma alta performance.

## Implicações da Arquitetura:
O MVC é uma arquitetura que separa a aplicação em três componentes principais, facilitando a gestão e escalabilidade do sistema. Se muitos usuários estão acessando os dados simultaneamente, pode-se otimizar o modelo de dados (Model) sem alterar a interface do usuário (View) ou a lógica de negócios (Controller). E utilizando o Node.js e Sails.js é possível lidar com várias requisições simultaneamente, o que é ótimo para escalabilidade em uma plataforma com usuários internacionais.
Quanto à manutenção, a separação clara entre as funções de cada componente do MVC facilita a manutenção já que é possível atualizar partes específicas da aplicação sem afetar as outras o que reduz o risco de introduzir bugs.
Assim como a manutenção, os testes podem ocorrer de forma independente, facilitando a identificação de erros e problemas principalmente com o Sails.js, que tem suporte para testes automatizados. Quanto à segurança, a separação no MVC ajuda a proteger e limitar o acesso aos dados através de diferentes níveis de autenticação e autorização nas Controllers. A arquitetura MVC também facilita a integração com outras interfaces e serviços, permitindo que a plataforma evolua e incorpore novas funcionalidades com menos dificuldades.
