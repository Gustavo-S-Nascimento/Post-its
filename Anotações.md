# Banco de dados 
Postgress / MariaDB 

Postgress - Projeto do Conduit (Codespace com Docker / Visual Studio Code Local)

MariaDB - Servidor de Fivem (phpMyAdmin com XAMPP)

## Postgress
**Motivo:** Estudo do curso de FullStack na [DigitalCollege](https://digitalcollege.com.br)  

<strong>Progresso:</strong>  
Feito o clone do repositorio [conduit](https://github.com/TonyMckes/conduit-realworld-example-app).  
Apresentado a ideia do que é o conduit e seu exemplo.  
Após um tempo de análise e estudo do código, foram feitas algumas perguntas para o mentor [Abraão Alves](https://github.com/AbraaoAlves).  
Passando para a pratica, o repositorio foi baixado para a maquina para ser trabalhado no VSCode local.  
Apresentado a extensão Postgresql Client 2.  
Foi rodado o seguinte comando no terminal.  
```bash
npm install
```
Depois de instalado todas as dependencias solicitadas, tentamos rodar o projeto.  
Passando apenas o comando. 
```bash
npm run dev 
```
O Frontend rodou normalmente com ajuda do [Vite](https://vitejs.dev).  
No Terminal acabou acontecendo um error no start do Backend.  
Erro causado pela comunicação do backend com as variáveis de ambiente.  
Notado que não existia o arquivo .env para propagar as a var'D Ambiente.  
Foi criado o mesmo e definido as var.  
Tentando novamente o projeto.  
O error mudou, porém continuava com um erro no backend.  
Não era possivel visualizar os posts, usuarios e tags.  
Também não era possivel fazer Login e Cadastro.  
Foi apresentado o restos dos comandos que deveriamos está fazendo.  
Seguindo a ordem desde o começo é:
```bash
npm i
```
```bash
npm run sqlz -- db:create
```
```bash
npm run dev
```
```bash
npm run sqlz -- db:seed:all
```
Rodando o projeto com todos os comandos listados o projeto startou com sucesso o backend.  
Passando para ser feito a conectividade com o banco de dados por meio da extensão.  
Visualizado pela a extensão do VSCode Postgresql Client 2.  
Após isso para questões de aprendizado o projeto foi forçado ao error.  
O error efetuado é sobre JWT.  
Foi explicado em como JWT é importante para a segurança e navegação por meio de headers.  

## MariaDB
**Motivo:** Um familiar proximo me pediu para colocar um "Celular" no [FiveM](https://fivem.net) (Uma distribuição do GTA V)  

**Pontos a considerar:** 
1. Servidor hosteado localmente.  
2. Sem muita complicação de dar o start.  
3. Sem muita complicação para tirar o banco de dados. (Caso não queira mais)  
4. Algo que dê para modificar caso venha ao caso.  

**Progresso:**  
Feito uma pesquisa por um celular que venha a funcionar sem um banco de dados.  
Foi achado o [KGV-Phone](https://github.com/Xinerki/kgv-phone).  
O mesmo foi colocado para um periodo de teste.  
Depois de um tempo foi me relatado os seguintes problemas:  
> 1. Devido a ser o celular original do jogo, é limitado.
>> 1-1. Só é possivel trocar mensagens com outros players quando eles estão na área do player atual.  
>> 1-2. Não é possivel fazer chamadas de voz com outros players.  
> 2. A Camera apresentava um error que as vezes resultava em um Crash no game.  
> 3. O design do celular não era muito legal.  
> 4. O Sistema de mensagens gerava uma notificação na interface do jogo porém não era intuitivo.  
>> 4-1. O Aplicativo de mensagens não deixava expandir e ler a mensagem que chegava, só era possivel ver no momento em que chegava a notificação.  
> 5. Alguns aplicativos não estavam em produção, ainda em desenvolvimento.  
>> 5-1. Existia um aplicativo desconhecido que estava apenas um icone escuro.

Foi decidido o descarte do celular atual.  
Na procura de outro celular achei o [NPWD](https://github.com/project-error/npwd).  
O mesmo funciona com o [screenshot-basic](https://github.com/project-error/screenshot-basic), [pma-voice](https://github.com/AvarianKnight/pma-voice), [oxmysql](https://github.com/overextended/oxmysql), [pe-core](https://github.com/project-error/pe-core) e um banco de dados.  
Como foi passado que tinha que ser algo mais "Simples", eu fui atrás de um banco de dados mais facil de ser colocado.  
Com a procura achei o [phpMyAdmin](https://www.phpmyadmin.net) que é um software para administração do MySQL pela Internet.  
Tendo auxilio do [XAMPP](https://www.apachefriends.org/pt_br/index.html) é possivel rodar um banco de dados online.  
o XAMPP faz o start no [Apache](https://www.apache.org) que é um servidor HTTP e no [mySQL](https://www.mysql.com) que é um banco de dados.  
Não tendo que está baixando nenhum dos dois software essa foi a opção que eu escolhi.  
Dando um start nos dois é só ir na opção de "Admin" do mySQL que nós é apresentado a tela inicial do phpMyAdmin.  
Tendo como base [MariaDB](https://mariadb.org) mexi um pouco para entender como funcionava o sistema.  
Fazendo toda a configuração do celular seguindo pelo o [tutorial](https://www.youtube.com/watch?v=3CLQeL1FBcM).  
Foi explicado de modo superficial, como funcionava e como ele poderia mexer.  
Dado o start e funcionando, foi submetido a um periodo de teste.  
Me apresentou os seguintes problemas:
> 1. A Câmera está dando um problema tirar a foto.
> 2. Não é possivel colocar foto de perfil nos aplicativos que tem essa opção.

### Extras
- Entrando no jogo para analisar melhor os problemas apresentados.
- Problema #1: apresentava o seguinte erro ao finalizar a foto "error: Create/update request failed".
- Problema #2: ao colocar a url da imagem apresentava um error que não é suportado esse formato.

No primeiro problema do NPWD foi notado que nos arquivos do celular, tinha um arquivo chamado "config.json".
Na abertura do mesmo e analisando o código, foi visto que as fotos estavam sendo feito o upload em "https://api.fivemanage.com/api/image".  
Indo mais fundo sobre essa api, foi notado que tinha que está fazendo um cadastro para usar em sua plenitude.  
Efetuado o cadastro foi me passado um Token para eu configurar no servidor.  
Após isso a câmera voltou a funcionar.


No segundo problema ainda no arquivo config.json e analisando o objeto chamado "imageSafety".  
O mesmo tinha uma key chamada "filterUnsafeImageUrls" que o valor era o boleano "True".  
Mudando esse valor para "False" ele aceitou todo tipo de URL.
