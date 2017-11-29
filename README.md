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
![Alt text](https://github.com/AcademiaMonstro/AcademiaMonstro-Trabalho-BD2/blob/master/Conceitual_1%20(2)F.png?raw=true "Modelo Conceitual")

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

![Alt text](https://github.com/AcademiaMonstro/AcademiaMonstro-Trabalho-BD2/blob/master/L%C3%B3gico_automaticoF.png?raw=true "Modelo Fisico")


### 7	MODELO FÍSICO<br>

CREATE TABLE Aluno (
    id SERIAL PRIMARY KEY,
    nome varchar(100) NOT NULL,
    login varchar(32) NOT NULL UNIQUE,
    senha varchar(32) NOT NULL,
    dt_nascimento date,
    active int default 1
);

CREATE TABLE Exercicio (
    id SERIAL PRIMARY KEY,
    nome varchar(45) NOT NULL UNIQUE,
    descricao varchar(100) NOT NULL,
    active int default 1
);

CREATE TABLE Restricao (
    nome varchar(45) NOT NULL UNIQUE,
    descricao varchar(100) NOT NULL,
    id SERIAL PRIMARY KEY,
    active int default 1
);

CREATE TABLE Musculo_Foco (
    id SERIAL PRIMARY KEY,
    nome varchar(45) NOT NULL,
    active int default 1
);

CREATE TABLE Objetivo (
    nome varchar(45) NOT NULL,
    id SERIAL PRIMARY KEY,
    active int default 1
);

CREATE TABLE Avaliador_Fisico (
    senha varchar(32) NOT NULL,
    nome varchar(100) NOT NULL,
    id SERIAL PRIMARY KEY,
    login varchar(32) NOT NULL UNIQUE,
    crm varchar(15) NOT NULL,
    active int default 1
);

CREATE TABLE Serie (
    descricao varchar(150) NOT NULL,
    id SERIAL PRIMARY KEY,
    dt_criacao DATE DEFAULT CURRENT_DATE,
    active int default 1
);

CREATE TABLE Instrutor (
    id SERIAL PRIMARY KEY,
    login varchar(32) NOT NULL UNIQUE,
    nome varchar(100) NOT NULL,
    senha varchar(32) NOT NULL,
    active int default 1
);

CREATE TABLE Medidas (
    id SERIAL PRIMARY KEY,
    medida int NOT NULL,
    dt_criacao DATE DEFAULT CURRENT_DATE,
    CONSTRAINT teste_medida_check CHECK (medida > 0),
    active int default 1
);

CREATE TABLE Tipo_Medidas (
    nome varchar(45) NOT NULL UNIQUE,
    id SERIAL PRIMARY KEY,
    active int default 1
);

CREATE TABLE Aluno_possui_Serie (
    FK_Aluno_id int NOT NULL,
    FK_Serie_id int NOT NULL,
    dt_criacao DATE DEFAULT CURRENT_DATE,
    active int default 1
);

CREATE TABLE Serie_possui_Objetivo (
    FK_Serie_id int NOT NULL,
    FK_Objetivo_id int NOT NULL,
    dt_criacao DATE DEFAULT CURRENT_DATE,
    active int default 1
);

CREATE TABLE Aluno_possui_Avaliador (
    FK_Aluno_id int NOT NULL,
    FK_Avaliador_Fisico_id int NOT NULL,
    dt_criacao DATE DEFAULT CURRENT_DATE,
    active int default 1
);

CREATE TABLE Serie_possui_Exercicio (
    FK_Exercicio_id int NOT NULL,
    FK_Serie_id int NOT NULL,
    dt_criacao DATE DEFAULT CURRENT_DATE,
    active int default 1
);

CREATE TABLE Aluno_possui_Instrutor (
    FK_Aluno_id int NOT NULL,
    FK_Instrutor_id int NOT NULL,
    dt_criacao DATE DEFAULT CURRENT_DATE,
    active int default 1
);

CREATE TABLE Serie_possui_Instrutor (
    FK_Instrutor_id int NOT NULL,
    FK_Serie_id int NOT NULL,
    dt_criacao DATE DEFAULT CURRENT_DATE,
    active int default 1
);

CREATE TABLE Exercicio_possui_Musculo (
    FK_Exercicio_id int NOT NULL,
    FK_Musculo_Foco_id int NOT NULL,
    dt_criacao DATE DEFAULT CURRENT_DATE,
    active int default 1
);

CREATE TABLE Objetivo_possui_Musculo (
    FK_Objetivo_id int NOT NULL,
    FK_Musculo_Foco_id int NOT NULL,
    active int default 1
);

CREATE TABLE Restricao_possui_Musculo (
    FK_Musculo_Foco_id int NOT NULL,
    FK_Restricao_id int NOT NULL,
    active int default 1
);

CREATE TABLE Aluno_possui_Restricao (
    FK_Aluno_id int NOT NULL,
    FK_Restricao_id int NOT NULL,
    dt_criacao DATE DEFAULT CURRENT_DATE,
    active int default 1
);

CREATE TABLE Exercicio_possui_Restricao (
    FK_Exercicio_id int NOT NULL,
    FK_Restricao_id int NOT NULL,
    active int default 1
);

CREATE TABLE Aluno_possui_Medidas (
    FK_Aluno_id int NOT NULL,
    FK_Medidas_id int NOT NULL,
    dt_criacao DATE DEFAULT CURRENT_DATE,
    active int default 1
);

CREATE TABLE Medidas_possui_Tipo (
    FK_Tipo_Medidas_id int NOT NULL,
    FK_Medidas_id int NOT NULL,
    active int default 1
);
 
ALTER TABLE Aluno_possui_Serie ADD CONSTRAINT FK_Aluno_possui_Serie_0
    FOREIGN KEY (FK_Aluno_id)
    REFERENCES Aluno (id)
    ON DELETE SET NULL ON UPDATE CASCADE;
 
ALTER TABLE Aluno_possui_Serie ADD CONSTRAINT FK_Aluno_possui_Serie_1
    FOREIGN KEY (FK_Serie_id)
    REFERENCES Serie (id)
    ON DELETE SET NULL ON UPDATE CASCADE;
 
ALTER TABLE Serie_possui_Objetivo ADD CONSTRAINT FK_Serie_possui_Objetivo_0
    FOREIGN KEY (FK_Serie_id)
    REFERENCES Serie (id)
    ON DELETE RESTRICT ON UPDATE RESTRICT;
 
ALTER TABLE Serie_possui_Objetivo ADD CONSTRAINT FK_Serie_possui_Objetivo_1
    FOREIGN KEY (FK_Objetivo_id)
    REFERENCES Objetivo (id)
    ON DELETE SET NULL ON UPDATE CASCADE;
 
ALTER TABLE Aluno_possui_Avaliador ADD CONSTRAINT FK_Aluno_possui_Avaliador_0
    FOREIGN KEY (FK_Aluno_id)
    REFERENCES Aluno (id)
    ON DELETE SET NULL ON UPDATE CASCADE;
 
ALTER TABLE Aluno_possui_Avaliador ADD CONSTRAINT FK_Aluno_possui_Avaliador_1
    FOREIGN KEY (FK_Avaliador_Fisico_id)
    REFERENCES Avaliador_Fisico (id)
    ON DELETE SET NULL ON UPDATE CASCADE;
 
ALTER TABLE Serie_possui_Exercicio ADD CONSTRAINT FK_Serie_possui_Exercicio_0
    FOREIGN KEY (FK_Exercicio_id)
    REFERENCES Exercicio (id)
    ON DELETE SET NULL ON UPDATE CASCADE;
 
ALTER TABLE Serie_possui_Exercicio ADD CONSTRAINT FK_Serie_possui_Exercicio_1
    FOREIGN KEY (FK_Serie_id)
    REFERENCES Serie (id)
    ON DELETE SET NULL ON UPDATE CASCADE;
 
ALTER TABLE Aluno_possui_Instrutor ADD CONSTRAINT FK_Aluno_possui_Instrutor_0
    FOREIGN KEY (FK_Aluno_id)
    REFERENCES Aluno (id)
    ON DELETE SET NULL ON UPDATE CASCADE;
 
ALTER TABLE Aluno_possui_Instrutor ADD CONSTRAINT FK_Aluno_possui_Instrutor_1
    FOREIGN KEY (FK_Instrutor_id)
    REFERENCES Instrutor (id)
    ON DELETE SET NULL ON UPDATE CASCADE;
 
ALTER TABLE Serie_possui_Instrutor ADD CONSTRAINT FK_Serie_possui_Instrutor_0
    FOREIGN KEY (FK_Instrutor_id)
    REFERENCES Instrutor (id)
    ON DELETE SET NULL ON UPDATE CASCADE;
 
ALTER TABLE Serie_possui_Instrutor ADD CONSTRAINT FK_Serie_possui_Instrutor_1
    FOREIGN KEY (FK_Serie_id)
    REFERENCES Serie (id)
    ON DELETE SET NULL ON UPDATE CASCADE;
 
ALTER TABLE Exercicio_possui_Musculo ADD CONSTRAINT FK_Exercicio_possui_Musculo_0
    FOREIGN KEY (FK_Exercicio_id)
    REFERENCES Exercicio (id)
    ON DELETE SET NULL ON UPDATE CASCADE;
 
ALTER TABLE Exercicio_possui_Musculo ADD CONSTRAINT FK_Exercicio_possui_Musculo_1
    FOREIGN KEY (FK_Musculo_Foco_id)
    REFERENCES Musculo_Foco (id)
    ON DELETE SET NULL ON UPDATE CASCADE;
 
ALTER TABLE Objetivo_possui_Musculo ADD CONSTRAINT FK_Objetivo_possui_Musculo_0
    FOREIGN KEY (FK_Objetivo_id)
    REFERENCES Objetivo (id)
    ON DELETE SET NULL ON UPDATE CASCADE;
 
ALTER TABLE Objetivo_possui_Musculo ADD CONSTRAINT FK_Objetivo_possui_Musculo_1
    FOREIGN KEY (FK_Musculo_Foco_id)
    REFERENCES Musculo_Foco (id)
    ON DELETE SET NULL ON UPDATE CASCADE;
 
ALTER TABLE Restricao_possui_Musculo ADD CONSTRAINT FK_Restricao_possui_Musculo_0
    FOREIGN KEY (FK_Musculo_Foco_id)
    REFERENCES Musculo_Foco (id)
    ON DELETE SET NULL ON UPDATE CASCADE;
 
ALTER TABLE Restricao_possui_Musculo ADD CONSTRAINT FK_Restricao_possui_Musculo_1
    FOREIGN KEY (FK_Restricao_id)
    REFERENCES Restricao (id)
    ON DELETE SET NULL ON UPDATE CASCADE;
 
ALTER TABLE Exercicio_possui_Restricao ADD CONSTRAINT FK_Exercicio_possui_Restricao_0
    FOREIGN KEY (FK_Exercicio_id)
    REFERENCES Exercicio (id)
    ON DELETE SET NULL ON UPDATE CASCADE;
 
ALTER TABLE Exercicio_possui_Restricao ADD CONSTRAINT FK_Exercicio_possui_Restricao_1
    FOREIGN KEY (FK_Restricao_id)
    REFERENCES Restricao (id)
    ON DELETE SET NULL ON UPDATE CASCADE;
 
ALTER TABLE Aluno_possui_Medidas ADD CONSTRAINT FK_Aluno_possui_Medidas_0
    FOREIGN KEY (FK_Aluno_id)
    REFERENCES Aluno (id)
    ON DELETE SET NULL ON UPDATE CASCADE;
 
ALTER TABLE Aluno_possui_Medidas ADD CONSTRAINT FK_Aluno_possui_Medidas_1
    FOREIGN KEY (FK_Medidas_id)
    REFERENCES Medidas (id)
    ON DELETE SET NULL ON UPDATE CASCADE;
 
ALTER TABLE Medidas_possui_Tipo ADD CONSTRAINT FK_Medidas_possui_Tipo_0
    FOREIGN KEY (FK_Tipo_Medidas_id)
    REFERENCES Tipo_Medidas (id)
    ON DELETE RESTRICT ON UPDATE RESTRICT;
 
ALTER TABLE Medidas_possui_Tipo ADD CONSTRAINT FK_Medidas_possui_Tipo_1
    FOREIGN KEY (FK_Medidas_id)
    REFERENCES Medidas (id)
    ON DELETE SET NULL ON UPDATE CASCADE;

ALTER TABLE Aluno_possui_Restricao ADD CONSTRAINT FK_Aluno_possui_Restricao_0
    FOREIGN KEY (FK_Aluno_id)
    REFERENCES Aluno (id)
    ON DELETE SET NULL ON UPDATE CASCADE;

ALTER TABLE Aluno_possui_Restricao ADD CONSTRAINT FK_Aluno_possui_Restricao_1
    FOREIGN KEY (FK_Restricao_id)
    REFERENCES Restricao (id)
    ON DELETE SET NULL ON UPDATE CASCADE;


### 8	INSERT APLICADO NAS TABELAS DO BANCO DE DADOS<br>
#### 8.1 DETALHAMENTO DAS INFORMAÇÕES        
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

![Alt text](https://github.com/AcademiaMonstro/AcademiaMonstro-Trabalho-BD2/blob/master/prints/select%2010/Screenshot_1.png?raw=true)
<br>
![Alt text](https://github.com/AcademiaMonstro/AcademiaMonstro-Trabalho-BD2/blob/master/prints/select%2010/alunorestricao.png?raw=true)
<br>
![Alt text](https://github.com/AcademiaMonstro/AcademiaMonstro-Trabalho-BD2/blob/master/prints/select%2010/avaliadorfisico.png?raw=true)
<br>
![Alt text](https://github.com/AcademiaMonstro/AcademiaMonstro-Trabalho-BD2/blob/master/prints/select%2010/exercicio.png?raw=true)
<br>
![Alt text](https://github.com/AcademiaMonstro/AcademiaMonstro-Trabalho-BD2/blob/master/prints/select%2010/instrutor.png?raw=true)
<br>
![Alt text](https://github.com/AcademiaMonstro/AcademiaMonstro-Trabalho-BD2/blob/master/prints/select%2010/medidas.png?raw=true)
<br>
![Alt text](https://github.com/AcademiaMonstro/AcademiaMonstro-Trabalho-BD2/blob/master/prints/select%2010/medidas.png?raw=true)
<br>
![Alt text](https://github.com/AcademiaMonstro/AcademiaMonstro-Trabalho-BD2/blob/master/prints/select%2010/restricao.png?raw=true)
<br>
![Alt text](https://github.com/AcademiaMonstro/AcademiaMonstro-Trabalho-BD2/blob/master/prints/select%2010/serie.png?raw=true)
<br>
![Alt text](https://github.com/AcademiaMonstro/AcademiaMonstro-Trabalho-BD2/blob/master/prints/select%2010/serie_exercicio.png?raw=true)
<br>
![Alt text](https://github.com/AcademiaMonstro/AcademiaMonstro-Trabalho-BD2/blob/master/prints/select%2010/tipo_medidas.png?raw=true)
<br><br><br>
		SELECT exercicio.nome,serie.descricao FROM serie_possui_exercicio
		INNER JOIN serie ON serie.id = serie_possui_exercicio.fk_serie_id
		INNER JOIN exercicio ON serie_possui_exercicio.fk_exercicio_id = exercicio.id
#### 9.3	SELECT DAS VISÕES COM PRIMEIROS 10 REGISTROS DA VIEW <br>
	
	<br> View utilizada para localizar os alunos com algum tipo de restrição <br>
	create view aluno_com_restricao as
	SELECT aluno.nome,restricao.nome as restricao,restricao.descricao FROM aluno_possui_restricao
	INNER JOIN aluno ON aluno.id = aluno_possui_restricao.fk_aluno_id
	INNER JOIN restricao ON aluno_possui_restricao.fk_restricao_id = restricao.id
	
	<br>
	select * from aluno_com_restricao <br>
	
![Alt text](https://github.com/AcademiaMonstro/AcademiaMonstro-Trabalho-BD2/blob/master/prints/consultaview.png?raw=true "View aluno_com_restricao")
        

#### 9.4	LISTA DE CODIGOS DAS FUNÇÕES, ASSERÇOES E TRIGGERS<br>

        CREATE OR REPLACE FUNCTION verifica_nomes()
	 RETURNS trigger AS
	'
		BEGIN
			IF EXISTS (Select * from objetivo where NEW.nome=nome) THEN 
			RAISE EXCEPTION ''Erro: Esse objetivo já existe.. tente outro nome!'';

			END IF;
			RETURN NULL;
		END;
	'
	LANGUAGE plpgsql;

	CREATE TRIGGER inseri_objetivos
	 BEFORE INSERT OR UPDATE ON objetivo
	 FOR EACH ROW
	EXECUTE PROCEDURE verifica_nomes();


![Alt text](https://github.com/AcademiaMonstro/AcademiaMonstro-Trabalho-BD2/blob/master/prints/trigger.png?raw=true "trigger")
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

### A criação de tabela e inclusão de dados foi realizada em um computador AMD-A8 7600 com 8GB de Ram e SSD SanDisk SDSSDA120G, utilizando-se do Windows 10 <br>

####<br>Para a criação da massa de dados foi criada uma aplicação em php, disponível no projeto.<br>

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

	CREATE INDEX idx_id ON Exercicio USING btree (id);                 
	CREATE INDEX idaluno_id ON Aluno USING btree (id);
	CREATE INDEX idrestricao_id ON Restricao USING btree (id);
	CREATE INDEX idmusculo_id ON Musculo_Foco USING btree (id);
	CREATE INDEX idobjetivo_id ON Objetivo USING btree (id);
	CREATE INDEX idavaliador_id ON Avaliador_Fisico USING btree (id);
	CREATE INDEX idinstrutor_id ON Instrutor USING btree (id);
	CREATE INDEX idmedidas_id ON Medidas USING btree (id);
	CREATE INDEX idtipo_id ON Tipo_Medidas USING btree (id);
	CREATE INDEX idx_id_aluno_serie ON Aluno_possui_Serie USING btree (FK_Aluno_id,FK_Serie_id);
	CREATE INDEX idx_id_serie_objetivo ON Serie_possui_Objetivo USING btree (FK_Objetivo_id,FK_Serie_id);
	CREATE INDEX idx_id_aluno_intrutor ON Aluno_possui_Instrutor USING btree (FK_Aluno_id,FK_Instrutor_id);
	CREATE INDEX idx_id_serie_exercicio_musculo ON Exercicio_possui_Musculo USING btree (FK_Exercicio_id,FK_Musculo_Foco_id);
	CREATE INDEX idx_id_serie_objetivo_musculo ON Objetivo_possui_Musculo USING btree (FK_Objetivo_id,FK_Musculo_Foco_id);
	CREATE INDEX idx_id_restricao_Musculo ON Restricao_possui_Musculo USING btree (FK_Musculo_Foco_id,FK_Restricao_id);
	CREATE INDEX idx_id_Aluno_possui_Restricao ON Aluno_possui_Restricao USING btree (FK_Aluno_id,FK_Restricao_id);
	CREATE INDEX idx_id_Exercicio_possui_Restricao ON Exercicio_possui_Restricao USING btree (FK_Exercicio_id,FK_Restricao_id);
	CREATE INDEX idx_id_aluno_Medidas ON Aluno_possui_Medidas USING btree (FK_Aluno_id,FK_Medidas_id);
	CREATE INDEX idx_id_medidas_Tipo ON Medidas_possui_Tipo USING btree (fk_tipo_medidas_id,fk_medidas_id);
	CREATE INDEX idx_id_serie_restricao_Musculoo ON Restricao_possui_Musculo USING btree (fk_musculo_foco_id,fk_restricao_id);
    
    
![Alt text](https://github.com/AcademiaMonstro/AcademiaMonstro-Trabalho-BD2/blob/master/prints/indexprints/criacao.png?raw=true)
<br><br>

Inserção de uma quantidade reduzida de dados, houve uma perda no desempenho, porém bem pequeno.

![Alt text](https://github.com/AcademiaMonstro/AcademiaMonstro-Trabalho-BD2/blob/master/prints/indexprints/instrutorindex.png?raw=true)
<br><br>

Inserção de uma quantidade volumosa de dados, houve uma perda bem significativa no desempenho.

![Alt text](https://github.com/AcademiaMonstro/AcademiaMonstro-Trabalho-BD2/blob/master/prints/indexprints/alunoindex.png?raw=true)
<br><br>

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



