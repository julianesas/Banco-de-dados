# Banco de dados

O banco de dados é a organização e armazenagem de informações sobre um domínio específico. De forma mais simples, é o agrupamento de dados que tratam do mesmo assunto, e que precisam ser armazenados para segurança ou conferência futura. 

SQL - é uma linguagem de consulta, onde você vai poder dar comandos, dar instruções ao meio ambiente do banco de dados, e ele vai te retornar uma "Query".
A linguagem SQL (Structured Query Language) é uma linguagem padrão para o gerenciamento de bancos de dados que seguem o modelo relacional.

SGBD - Sistema gerenciador de banco de dados. 

Banco de dados contêm tabelas, tabelas contêm registros e registros contêm campos.

## DDL (Data Definition Language)

Os comandos do tipo DDL (Data Definition Language) são utilizados para gerenciar a estrutura do banco de dados. Sendo assim, eles nos permitem alterar a estrutura de um objeto do banco, além de serem usados para criar e excluir tabelas.

### Create -criando novos bancos de dados e novas tabelas

O comando abaixo vai criar um banco de dados chamado 'banco'

``` 
create database banco;
```

O comando abaixo vai criar um banco de dados chamado 'banco'

``` 
create database banco;
```

melhorando o comando ´create database`, setando o utf 8 como codificador de characters especiais:

``` 
create database banco
default character set utf8
default collate utf8_general_ci;
```


O comando abaixo vai criar uma tabelas cursos, caso ela não exista; 

``` 
create tables if not exists cursos(
nome varchar(30) not null unique,
descricao text,
carga int unsigned,
totaulas int unsigned,
ano year default '2016'
) default charset = utf8;
```

### ALTER: alterando uma tabela já criada

O comando abaixo, cria uma nova coluna com o nome profissão:

```
alter table pessoas
add column profissao varchar(30);
```
O comando abaixo, apaga a coluna com o nome profissão:

```
alter table pessoas
drop column profissao;
```

O comando abaixo, adiciona a coluna 'profissao' após a coluna 'nome':
```
alter table pessoas
add column profissao varchar(10) after nome;
```

Adicionar a coluna código como a primeira coluna:
```
alter table pessoas
add column codigo int first;
```

o comando abaixo modifica as constraints e os tipos primitivos, porém não pode renomear a coluna:
```
alter table pessoas
modify column profissao varchar (20) not null;
```

o comando abaixo modifica o nome da coluna,  as constraints e os tipos primitivos, porém você precisa colocar o nome anterior da coluna e o atual:
```
alter table pessoas
change column profissao prof varchar (20);
```

o comando abaixo modifica o nome da tabela 'pessoas' para 'gafanhotos':
```
alter table pessoas
rename to gafanhotos;
```

e se depois eu quiser inserir uma coluna para a minha primary key? é simple:

```
alter table pessoas
add column idcurso int first;
```
```
alter table pessoas
add primary key (idcurso);
```

### DROP: excluindo uma tabela do banco de dados

O comando abaixo exclue a base de dados 'banco':

```
drop database banco;
```

O comando abaixo exclue a tabela 'cursos':

```
drop table cursos;
```

```
alter table pessoas
add primary key (idcurso);
```






## DML (Data Manipulation Language)

É um subconjunto da linguagem SQL que comporta os comandos utilizados para manipular diretamente os dados. Ou seja, por meio deles, é possível realizar ações como inserir informações em uma tabela, realizar consultas, deletar e alterar os registros. 

### INSERT: adicionando registros a uma tabela

``` 
insert into pessoas
(nome, nascimento, sexo, peso, altura nacionalidade)
values
('Gordofredo','1984-01-03','M','78.5','1.83','Brasil');
```

Caso você estiver inserindo dados, e os dados estiverem na ordem das colunas das tabelas, você pode omitir os nomes das colunas, ex:


``` 
insert into pessoas values
('Gordofredo','1984-01-03','M','78.5','1.83','Brasil');
```

Também pode inserir várias pessoas em um único comando:

``` 
insert into pessoas values
('Gordofredo','1984-01-03','M','78.5','1.83','Brasil'),
('Pedro','1984-01-03','M','78.5','1.83','Brasil');
```

### UPDATE: atualizando os registros já inseridos

O exemplo abaixo estará atualizando a tabela cursos, alterando o campo 'nome' para HTML5 onde o campo 'idcurso' for igual a 1


``` 
update cursos
set nome = 'html5'
where idcurso='1';
```

Caso dê problema de segurança, você pode utilizar o comando 
`set sql_safe_updates=0;` => antes do comando update
`set sql_safe_updates=1;` => Depois do comando update

Para limitar a quantidade de linhas que você quer afetar use o `limit`:

``` 
update cursos
set nome = 'html5'
where idcurso='1'
limit 1;
```

### DELETE: excluindo registros de uma tabela

O exemplo abaixo estará deletando da tabela cursos, o registro que possui o idcurso = 8:

``` 
delete from cursos
where idcurso='8'
limit 1;
```

### Truncate: excluindo todas linhas de uma tabela

O exemplo abaixo irá apagar todos as linhas da tabela cursos:

``` 
truncate table cursos;
```

### SELECT: retomando registros na tabela

O SELECT é um dos comandos SQL mais importantes, pois com ele podemos elaborar diversas consultas aos registros da nossa base de dados.

o comando abaixo retornará tudo da tabela cursos:

``` 
select * from cursos;
```

o comando abaixo retornará tudo da tabela cursos:

``` 
select * from cursos;
```

Para fazer buscas mais específicas:
``` 
select nome, carga from cursos;
``` 
Seleciona o nome dos estudantes  que forem do curso de Desenvolvimento de software:
```
SELECT nome FROM estudantes WHERE curso = 'Desenvolvimento de Software';
```

O comando abaixo fará com que os nomes sejam exibidos de forma ascendentes:
```
SELECT nome FROM estudantes ORDER BY nome;
```












