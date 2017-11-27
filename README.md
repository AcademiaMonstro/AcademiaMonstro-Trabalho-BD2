# TRABALHO 01 : Academia Monstro
Trabalho desenvolvido durante a disciplina de BD

# Sumário

### 1	COMPONENTES<br>

Douglas Campos Sutil

Lucas Dipré Pereira

### 2	INTRODUÇÃO E MOTIVAÇAO<br>
Este documento contém a especificação do projeto do banco de dados da uma Academia de Monstro, que tem como objetivo modelar um sistema de criação, monitoramento e registro de exercícios fisicos para os alunos de uma academia, visando otimizar os treinamentos de acordo com as necessidades do aluno com um acompanhamento mais próximo do professor por meio das informações obtidas nos treinos  <br>
      
### 3	MINI-MUNDO<br>
O “Academia Monstro” é um software de gestão de exercícios de academia preparado para gerir e fiscalizar todas as séries de exercícios recomendadas para os frequentadores da academia. Com interfaces amigáveis e de fácil uso para criação de séries, é possível também controlar turmas com quantidades específicas de alunos por horários.

Além disso, o “Academia Monstrão” possui módulos específicos para atender diferentes necessidades. As ferramentas de montagem de treinos, por exemplo, são práticas e ajudam a proporcionar um atendimento de qualidade, com um gasto de tempo muito menor, enquanto você amplia o relacionamento com seus alunos por meio dos aplicativos integrados às atividades desenvolvidas na academia.

O sistema possui 4 tipos diferentes de categorias de usuários: Recepção,Aluno,Instrutor e Médico.

O usuário do tipo “Recepção”, entrará com as informações de cadastros iniciais do aluno.

A categoria “Aluno” terá acesso à série recomendada, histórico de evolução dos exercícios, histórico de mudanças das medidas do seu corpo, além da possibilidade de inserir espécies de anotações nos exercícios praticados naquele determinado dia (peso e repetições praticadas naquele dia).

Já o “Instrutor” poderá criar/editar/visualizar as séries de exercícios de todos os seus “Alunos”, além do acesso ao histórico para o monitoramento da evolução do mesmo.

O “Médico” basicamente irá inserir as métricas do aluno, além de apontar as restrições que cada um terá.

Dentro da academia, o “Academia Monstrão” funciona sem depender da velocidade ou estabilidade da internet. Assim, é possível manter o software de gestão de exercícios sempre ativo, com ou sem conexão. Mas é possível também acessar o sistema de qualquer lugar, com um aplicativo que se conecta com o servidor da academia, basta estar conectado a uma rede. <br>

### 4	RASCUNHOS BÁSICOS DA INTERFACE (MOCKUPS)<br>

![Alt text](https://github.com/AcademiaMonstro/AcademiaMonstro-Trabalho-BD2/blob/master/Tela%20de%20Login%20do%20Aluno.png)
![Alt text](https://github.com/AcademiaMonstro/AcademiaMonstro-Trabalho-BD2/blob/master/Tela%20de%20Cadastro%20do%20Aluno.png)
![Alt text](https://github.com/AcademiaMonstro/AcademiaMonstro-Trabalho-BD2/blob/master/Tela%20de%20Treino%20Usuario.png)
![Alt text](https://github.com/AcademiaMonstro/AcademiaMonstro-Trabalho-BD2/blob/master/Tela%20do%20Professor%20de%20Cria%C3%A7%C3%A3o%20de%20S%C3%A9rie%20de%20Exercicios.png)
![Alt text](https://github.com/AcademiaMonstro/AcademiaMonstro-Trabalho-BD2/blob/master/Tela%20do%20professor%20de%20Atividade%20do%20Aluno.png)
![Alt text](https://github.com/AcademiaMonstro/AcademiaMonstro-Trabalho-BD2/blob/master/Tela%20de%20Exame%20do%20M%C3%A9dico.png)


### 5	MODELO CONCEITUAL<br>
#### 5.1 NOTACAO ENTIDADE RELACIONAMENTO
![Alt text](https://github.com/AcademiaMonstro/AcademiaMonstro-Trabalho-BD2/blob/master/Conceitual_1.png?raw=true "Modelo Conceitual")

#### 5.3 DECISÕES DE PROJETO

	Regras de Relacionamento N:N – Para estabelecer este tipo de relacionamento, devemos ter três tabelas, <br>
	sendo que a terceira é responsável por relacionar as outras duas. Para isso, é preciso que essas duas <br>
	primeiras tabelas contenham uma coluna que seja chave primária.<br>
	As colunas que são chaves primárias na primeira e na segunda tabela devem ser colunas com chave estrangeira <br>
	na terceira. Assim, esta tabela terá duas chaves estrangeiras, as quais formam uma chave primária composta.<br>
	
    [atributo]: [descrição da decisão]
    
    EXEMPLO:
    a) Campo endereço: em nosso projeto optamos por um campo multivalorado e composto, pois a empresa 
    pode possuir para cada departamento mais de uma localização... 
    b) justifique!

#### 5.4 DESCRIÇÃO DOS DADOS 

Medidas:Tabela que armazena as informações relativas às medidas físicas do aluno <br>
	id:código único utilizado para identificar o conjunto de informações da tabela <br>
	peso:campo que armazena o peso do aluno em kg <br>
	altura:campo que armazena o altura do aluno em cm <br>
	cintura:campo que armazena o tamanho da cintura do aluno em cm <br>
	biceps:campo que armazena o tamanho do bíceps do aluno em cm <br>
	dt_medicao:campo que armazena data de medição das métricas do aluno <br>


Exercicio:Tabela que armazena as informações relativas aos exercícios que poderam ser exercutados por alunos <br>
	id:código único utilizado para identificar o conjunto de informações da tabela <br>
	nome:campo que armazena o nome do exercicio <br>
	descricao:campo que armazena uma breve descrição do exercicio <br>

Serie: Tabela que armazena as informações relativas à séries(combinação de exercícios) criadas para cada aluno <br>
	id:código único utilizado para identificar o conjunto de informações da tabela<br>
	id_instrutor: código identificador da relação entre a série e quem a criou<br>
	descricao:campo que armazena uma breve descrição do conjunto de exercícios<br>

Restricoes: Tabela que armazena as informações relativas às restrições físicas <br>
do aluno para que não seja recomendado exercícios prejudiciais ao aluno <br>
	id:código único utilizado para identificar o conjunto de informações da tabela<br>
	nome: campo que armazena o nome da restrição<br>
	descricao:campo que armazena uma breve descrição da restrição do aluno<br>

Musculo_Foco: Tabela que armazena as informações relativas aos músculos do corpo humano <br>
	id:código único utilizado para identificar o conjunto de informações da tabela<br>
	nome: campo que armazena o nome do músculo foco<br>

Objetivos: Tabela que armazena as informações relativas aos objetivos do aluno <br>
no que se refere ao condicionamento físico <br>
	id:código único utilizado para identificar o conjunto de informações da tabela<br>
	nome: campo que armazena o objetivo do aluno ou do exercício<br>

Avaliador_Fisico:Tabela que armazena as informações relativas ao avaliador físico <br>
	id:código único utilizado para identificar o conjunto de informações da tabela<br>
	nome: campo que armazena o nome do avaliador físico<br>
	login:campo que armazena o login no formato md5 do avaliador físico<br>
	senha: campo que armazena a senha no formato md5 do avaliador físico<br>
	crm: campo que armazena o crm do avaliador físico<br>

Instrutor:Tabela que armazena as informações relativas ao instrutor <br>
	id:código único utilizado para identificar o conjunto de informações da tabela<br>
	nome: campo que armazena o nome do Instrutor<br>
	login:campo que armazena o login no formato md5 do Instrutor<br>
	senha: campo que armazena a senha no formato md5 do Instrutor<br>
	
Aluno:Tabela que armazena as informações relativas ao aluno incluindo os as <br>
referências à outras tabelas que complementam as informações necessárias para <br>
uma boa criação de série de exercícios para cada praticante <br>
	id:código único utilizado para identificar o conjunto de informações da tabela<br>
	nome: campo que armazena o nome do Aluno<br>
	login:campo que armazena o login no formato md5 do Aluno<br>
	senha: campo que armazena a senha no formato md5 do Aluno<br>
	dt_nascimento: campo que armazena a data de nascimento do Aluno<br>
	id_medidas: código identificador da relação entre o Aluno e suas medidas<br>
	id_restricoes: código identificador da relação entre o Aluno e suas restrições (se possuir)<br>
	id_instrutor: código identificador da relação entre o Aluno e seu instrutor<br>
	id_avaliador: código identificador da relação entre o Aluno e seu avaliador físico<br>



### 6	MODELO LÓGICO<br>
### 7	MODELO FÍSICO<br>

![Alt text](https://github.com/AcademiaMonstro/AcademiaMonstro-Trabalho-BD2/blob/master/png_bd.png?raw=true "Modelo Fisico")


### 8	INSERT APLICADO NAS TABELAS DO BANCO DE DADOS<br>
#### 8.1 DETALHAMENTO DAS INFORMAÇÕES
        Detalhamento sobre as informações e processo de obtenção ou geração dos dados.
        Referenciar todas as fontes referentes a:
        a) obtenção dos dados
        b) obtenção de códigos reutilizados
        c) fontes de estudo para desenvolvimento do projeto
        
#### 8.2 INCLUSÃO DO SCRIPT PARA CRIAÇÃO DE TABELAS E INSERÇÃO DOS DADOS (ARQUIVO ÚNICO COM):
        a) inclusão das instruções para criação das tabelas e estruturas de amazenamento do BD
CREATE TABLE Medidas(
	id int primary key unique,
	peso real not null,
	altura real not null,
	cintura real not null,
	dt_medicao date default CURRENT_DATE	
);

CREATE TABLE Restricoes(
	id int primary key unique,
	nome varchar(45) not null,
	descricao varchar(150) not null
);

CREATE TABLE Exercicio(
	id int primary key unique,
	nome varchar(50) not null,
	descricao varchar(150) not null
);

CREATE TABLE Objetivos(
	id int primary key unique,
	nome varchar(150) not null
);

CREATE TABLE Musculo_Foco(
	id int primary key unique,
	nome varchar(45) not null
);

CREATE TABLE Avaliador_Fisico(
	id int primary key unique,
	nome varchar(50) not null,
	crm varchar(50) not null,
	login varchar(32) not null ,
	senha varchar(32) not null
);

CREATE TABLE Instrutor(
	id int primary key unique,
	nome varchar(50) not null,
	login varchar(32) not null ,
	senha varchar(32) not null
);

CREATE TABLE Serie(
	id int primary key unique,
	descricao varchar(150) not null,
	id_instrutor int,

	foreign key (id_instrutor) references Instrutor(id)	
);

CREATE TABLE Aluno(
	id int primary key unique,
	nome varchar(50) not null,
	login varchar(32) not null ,
	senha varchar(32) not null,
	dt_nascimento date not null,
	id_medidas int,
	id_restricoes int,
	id_instrutor int,
	id_avaliador int,
	
	foreign key (id_medidas) references Medidas(id),
	foreign key (id_restricoes) references Restricoes(id),
	foreign key (id_instrutor) references Instrutor(id),
	foreign key (id_avaliador) references Avaliador_Fisico(id)	
);

CREATE TABLE Aluno_Serie(
	id_aluno int,
	id_serie int,
	dt_criacao date default CURRENT_DATE,
	dt_final date not null,

	foreign key (id_aluno) references Aluno(id),
	foreign key (id_serie) references Serie(id)	
);

CREATE TABLE Exercicio_Musculo(
	id_exercicio int,
	id_musculo_foco int,

	foreign key (id_exercicio) references Exercicio(id),
	foreign key (id_musculo_foco) references Musculo_Foco(id)	
);

CREATE TABLE Objetivo_Aluno(
	id_objetivo int,
	id_aluno int,

	foreign key (id_objetivo) references Objetivos(id),
	foreign key (id_aluno) references Aluno(id)	
);

CREATE TABLE Objetivo_Musculo(
	id_objetivo int,
	id_musculo int,

	foreign key (id_objetivo) references Objetivos(id),
	foreign key (id_musculo) references Musculo_Foco(id)	
);

CREATE TABLE Restricoes_Musculo(
	id_restricoes int,
	id_musculo int,

	foreign key (id_restricoes) references Restricoes(id),
	foreign key (id_musculo) references Musculo_Foco(id)	
);

CREATE TABLE Serie_Exercicio(
	id_exercicio int,
	id_serie int,
	peso int not null,
	repeticao int not null,

	foreign key (id_exercicio) references Exercicio(id),
	foreign key (id_serie) references Serie(id)	
);

CREATE TABLE Serie_Objetivo(
	id_objetivo int,
	id_serie int,

	foreign key (id_objetivo) references Objetivos(id),
	foreign key (id_serie) references Serie(id)	
);
        
        b) inclusão das instruções de inserção dos dados nas referidas tabelas
        
INSERT INTO exercicio (id, nome, descricao) 
VALUES(1, 'Agachamento', 'abaixar até angulo de 90º e subir');

INSERT INTO instrutor (id, nome, login, senha) 
VALUES(1, 'João', 'Abacaxi', 'Abacaxi');

INSERT INTO medidas (id, peso, altura, cintura) 
VALUES(1,70, 160, 160);

INSERT INTO serie (id,descricao, id_instrutor) 
VALUES(1,'engrossar pernas', 1);

INSERT INTO restricoes (id,nome, descricao) 
VALUES(1,'joelho','ligamento operado recentemente');

INSERT INTO objetivos (id,nome) 
VALUES(1,'engrossar pernas');

INSERT INTO musculo_foco (id,nome) 
VALUES(1,'quadríceps');

INSERT INTO avaliador_fisico (id, nome, login, senha, crm) 
VALUES(1, 'João', 'Abacaxi', 'Abacaxi','pms2017es');

INSERT INTO aluno (id, nome, login, senha,dt_nascimento,id_medidas,
		   id_restricoes,id_instrutor,id_avaliador) 
VALUES(1, 'João', 'Abacaxi', 'Abacaxi','1990-07-07',1,1,1,1);.

INSERT INTO aluno_serie (id_aluno,id_serie,dt_final) 
VALUES(1,1,'2017-10-26');

INSERT INTO exercicio_musculo (id_exercicio,id_musculo_foco) 
VALUES(1,1);

INSERT INTO objetivo_aluno (id_objetivo,id_aluno) 
VALUES(1,1);

INSERT INTO objetivo_musculo (id_objetivo,id_musculo) 
VALUES(1,1);

INSERT INTO restricoes_musculo (id_restricoes,id_musculo) 
VALUES(1,1);

INSERT INTO serie_exercicio (id_serie,id_exercicio,peso,repeticao) 
VALUES(1,1,10,10);

INSERT INTO serie_objetivo (id_serie,id_objetivo) 
VALUES(1,1);

        
        c) inclusão das instruções para execução de outros procedimentos necessários

### 9	TABELAS E PRINCIPAIS CONSULTAS<br>
#### 9.1	GERACAO DE DADOS (MÍNIMO DE 10 REGISTROS PARA CADA TABELA NO BANCO DE DADOS)<br>

## Data de Entrega: (18/09/2017)

<br>
OBS: Incluir para os tópicos 9.2 e 9.3 as instruções SQL + imagens (print da tela) mostrando os resultados.<br>

#### 9.2	SELECT DAS TABELAS COM PRIMEIROS 10 REGISTROS INSERIDOS <br> 
    Data de Entrega: (Data a ser definida)
<br>

#### 9.3	SELECT DAS VISÕES COM PRIMEIROS 10 REGISTROS DA VIEW <br>
        a) Descrição da view sobre que grupos de usuários (operacional/estratégico) <br>
        e necessidade ela contempla.
        b) Descrição das permissões de acesso e usuários correlacionados (após definição <br>
        destas características)
    Data de Entrega: (Data a ser definida)
<br>

#### 9.4	LISTA DE CODIGOS DAS FUNÇÕES, ASSERÇOES E TRIGGERS<br>
        Detalhamento sobre funcionalidade de cada código.
        a) Objetivo
        b) Código do objeto (função/trigger/asserção)
        c) exemplo de dados para aplicação
        d) resultados em forma de tabela/imagem
<br>

#### 9.5	Administração do banco de dados<br>
        Descrição detalhada sobre como serão executadas no banco de dados as <br>
        seguintes atividades.
        a) Segurança e autorização de acesso:
        b) Estimativas de aquisição de recursos para armazenamento e processamento da informação
        c) Planejamento de rotinas de manutenção e monitoramento do banco
        d) Plano com frequencia de análises visando otimização de performance
<br>

#### 9.6	GERACAO DE DADOS (MÍNIMO DE 1,5 MILHÃO DE REGISTROS PARA PRINCIPAL RELAÇAO)<br>

## A criação de tabela e inclusão de dados foi realizada em um computador AMD-A8 7600 com 8GB de Ram e SSD SanDisk SDSSDA120G, utilizando-se do Windows 10 <br>

<br> CRIAÇÃO DO BANCO DE DADOS <br>

![Alt text](https://github.com/AcademiaMonstro/AcademiaMonstro-Trabalho-BD2/blob/master/prints/CRIACAO_TABELA.png?raw=true "CRIAÇÃO DO BANCO")

<br> INSERÇÃO DE 1,5 MILHÕES DE REGISTROS TABELA ALUNO <br>

![Alt text](https://github.com/AcademiaMonstro/AcademiaMonstro-Trabalho-BD2/blob/master/prints/ALUNO.png?raw=true "ALUNO")

<br> INSERÇÃO DE REGISTROS TABELA RESTRICAO <br>

![Alt text](https://github.com/AcademiaMonstro/AcademiaMonstro-Trabalho-BD2/blob/master/prints/RESTRICAO.png?raw=true "RESTRICAO")

<br> INSERÇÃO DE REGISTROS TABELA ALUNO_POSSUI_RESTRICAO <br>

![Alt text](https://github.com/AcademiaMonstro/AcademiaMonstro-Trabalho-BD2/blob/master/prints/ALUNORESTRICAO.png?raw=true "ALUNORESTRICAO")

<br> INSERÇÃO DE REGISTROS TABELA EXERCICIO <br>

![Alt text](https://github.com/AcademiaMonstro/AcademiaMonstro-Trabalho-BD2/blob/master/prints/EXERCICIO.png?raw=true "EXERCICIO")

<br> INSERÇÃO DE REGISTROS TABELA SERIE <br>

![Alt text](https://github.com/AcademiaMonstro/AcademiaMonstro-Trabalho-BD2/blob/master/prints/SERIE.png?raw=true "SERIE")

<br> INSERÇÃO DE REGISTROS TABELA SERIE_POSSUI_EXERCICIO <br>

![Alt text](https://github.com/AcademiaMonstro/AcademiaMonstro-Trabalho-BD2/blob/master/prints/SERIEEXERCICIO.png?raw=true "SERIEEXERCICIO")

<br> INSERÇÃO DE REGISTROS TABELA INSTRUTOR <br>

![Alt text](https://github.com/AcademiaMonstro/AcademiaMonstro-Trabalho-BD2/blob/master/prints/INSTRUTOR.png?raw=true "INSTRUTOR")

<br> INSERÇÃO  DE REGISTROS TABELA MEDIDAS <br>

![Alt text](https://github.com/AcademiaMonstro/AcademiaMonstro-Trabalho-BD2/blob/master/prints/MEDIDAS.png?raw=true "MEDIDAS")

<br> INSERÇÃO DE REGISTROS TABELA TIPO_MEDIDAS <br>

![Alt text](https://github.com/AcademiaMonstro/AcademiaMonstro-Trabalho-BD2/blob/master/prints/TIPOMEDIDAS.png?raw=true "TIPOMEDIDAS")

<br> INSERÇÃO DE REGISTROS TABELA AVALIADOR_FISICO <br>

![Alt text](https://github.com/AcademiaMonstro/AcademiaMonstro-Trabalho-BD2/blob/master/prints/AVALIADORFISICO.png?raw=true "AVALIADORFISICO")

        


#### 9.7	Backup do Banco de Dados<br>
        Detalhamento do backup.
        a) Tempo
        b) Tamanho
        c) Teste de restauração (backup)
        d) Tempo para restauração
        e) Teste de restauração (script sql)
        f) Tempo para restauração (script sql)
<br>

Data de Entrega: (Data a ser definida)
<br>

#### 9.8	APLICAÇAO DE ÍNDICES E TESTES DE PERFORMANCE<br>
    a) Lista de índices, tipos de índices com explicação de porque foram implementados
    b) Performance esperada VS Resultados obtidos
    c) Tabela de resultados comparando velocidades antes e depois da aplicação dos índices.
<br>
    Data de Entrega: (Data a ser definida)
<br>   

#### 9.9	ANÁLISE DOS DADOS COM ORANGE<br>    
        a) captura das informaçõs
        b) integração com banco de dados em desenvolvimento
        c) aplicação de algoritmos e interpretação dos resultados
        c) atualização da documentação do trabalho incluindo a mineração de dados
<br>
    Data de Entrega: (Data a ser definida)
<br>

### 10	ATUALIZAÇÃO DA DOCUMENTAÇÃO/ SLIDES E ENTREGA FINAL<br>
<br>
    Data de Entrega: (Data a ser definida)
<br>

### 11	DIFICULDADES ENCONTRADAS PELO GRUPO<br>  

       
### 12  FORMATACAO NO GIT: https://help.github.com/articles/basic-writing-and-formatting-syntax/
<comentario no git>
    
##### About Formatting
    https://help.github.com/articles/about-writing-and-formatting-on-github/
    
##### Basic Formatting in Git
    
    https://help.github.com/articles/basic-writing-and-formatting-syntax/#referencing-issues-and-pull-requests
    
    
##### Working with advanced formatting
    https://help.github.com/articles/working-with-advanced-formatting/
#### Mastering Markdown
    https://guides.github.com/features/mastering-markdown/

### OBSERVAÇÕES IMPORTANTES

#### Todos os arquivos que fazem parte do projeto (Imagens, pdfs, arquivos fonte, etc..), devem estar presentes no GIT. Os arquivos do projeto vigente não devem ser armazenados em quaisquer outras plataformas.
1. Caso existam arquivos com conteúdos sigilosos, comunicar o professor que definirá em conjunto com o grupo a melhor forma de armazenamento do arquivo.

#### Todos os grupos deverão fazer Fork deste repositório e dar permissões administrativas ao usuário deste GIT, para acompanhamento do trabalho.

#### Os usuários criados no GIT devem possuir o nome de identificação do aluno (não serão aceitos nomes como Eu123, meuprojeto, pro456, etc). Em caso de dúvida comunicar o professor.


Link para BrModelo:<br>
http://sis4.com/brModelo/brModelo/download.html
<br>


Link para curso de GIT<br>
![https://www.youtube.com/curso_git](https://www.youtube.com/playlist?list=PLo7sFyCeiGUdIyEmHdfbuD2eR4XPDqnN2?raw=true "Title")



