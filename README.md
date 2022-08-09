# testealo
12
# 👌 SQL ORACLE

Como já mencionado, temos no SQL comandos de consultas (queries) e ao realizar essa consulta precisamos definir em quais tabelas gostaríamos de buscar essas informações. Caso esses dados que queremos, esteja apenas em uma tabela, basta incluir o nome dela. Já se essas informações estiverem em mais de uma tabela, será necessário utilizar a cláusula Join.

O Join une as tabelas através de um critério, ao elaborar essa consulta que junta tabelas podemos definir filtros, tal como clientes apenas no sexo masculino e/ou que moram apenas na região Sul. Essa consulta que aplicamos o filtro pode ser uma view.

Internamente, o banco de dados possuem as procedures. No começo desse treinamento havia mencionado que a linguagem SQL não é estruturada, mas a partir disso os estudiosos de banco de dados MySQL, Oracle e SQL Server criaram linguagens que não estão mais no padrão ANSI, mas linguagens proprietárias que permitem utilizar comando SQL para fazer algum tipo de lógica estruturada com if, while, entre outros comandos de repetições, por exemplo. Como se tivéssemos um programa em uma linguagem nativa do banco de dados utilizando comando SQL.

Nas procedures, podemos ter as funções. Estas são cálculos montados com campos que podemos usar dentro de um comando de consulta. Podemos criar uma função que facilite uma visualização ou contabilização e usa-lá para realizar as consultas.

O próprio banco MySQL possui um catálogo de funções: como tirar espaços em branco do registro, transformar letra maiúscula em minúscula, efetuar cálculos complexos como de datas — quantos dias tem entre determinadas datas, entre outras funções.

No banco de dados, também, temos o trigger. Este é um aviso programado caso algo ocorra no banco de dados ou tabela. Como, se quisermos ser avisados caso alguém realize alguma alteração ou delete informações nas tabelas. Este aviso poder ser uma função, uma procedure ou um único comando SQL, que será executado quando a condição da trigger for satisfeita.

Exemplificando, se tivermos duas tabelas "tabela_clientes" e a "tabela_taxas". Todo cliente cadastrado é preciso ir à tabela taxas e criar uma taxa com o valor zero na "tabela_taxas". Podemos ter uma trigger que toda vez que criado um cadastro na tabela de cliente, irá à tabela de taxas inserir o código do cliente e mais uma taxa default (padrão).

COLUMNS = COLUNAS

INDEXES = ÍNDICES

FOREIGN KEYS = CHAVE ESTRANGEIRA

TRIGGERS = GATILHO (DEFAULT)

COMANDO: SELECT * FROM city;

SELECT * FROM COUNTY

# Para utilizar um campo e puxar a informação em tabela de uma condição menor que uma porcentagem, utiliza-se:

`SELECT * FROM **TABELA_DE_VENDEDORES** WHERE **PERCENTUAL_COMISSAO > 0.10;**`

# Veja quais são os vendedores que foram admitidos da empresa a partir de 2016:

`SELECT * FROM TABELA_DE_VENDEDORES WHERE YEAR(DATA_ADMISSAO) >= 2016;`

# Veja quais são os vendedores que estão de férias e que foram admitidos antes de 2016:

`SELECT * FROM TABELA_DE_VENDEDORES WHERE YEAR(DATA_ADMISSAO) < 2016 AND DE_FERIAS = 1;`

# 

1. Acesse o Workbench e crie um novo script SQL.
2. Abra o arquivo SQL_10.sql e execute o script. As tabelas serão apagadas, recriadas e novos registros serão incluídos. O conteúdo do script é reproduzido abaixo.

```sql
USE sucos;

DROP TABLE tbcliente;

DROP TABLE tbproduto;

CREATE TABLE tbcliente
( CPF VARCHAR (11) ,
NOME VARCHAR (100) ,
ENDERECO1 VARCHAR (150) ,
ENDERECO2 VARCHAR (150) ,
BAIRRO VARCHAR (50) ,
CIDADE VARCHAR (50) ,
ESTADO VARCHAR (2) ,
CEP VARCHAR (8) ,
DATA_NASCIMENTO DATE,
IDADE SMALLINT,
SEXO VARCHAR (1) ,
LIMITE_CREDITO FLOAT ,
VOLUME_COMPRA FLOAT ,
PRIMEIRA_COMPRA BIT );

ALTER TABLE tbcliente ADD PRIMARY KEY (CPF);

CREATE TABLE tbproduto
(PRODUTO VARCHAR (20) ,
NOME VARCHAR (150) ,
EMBALAGEM VARCHAR (50) ,
TAMANHO VARCHAR (50) ,
SABOR VARCHAR (50) ,
PRECO_LISTA FLOAT);

ALTER TABLE tbproduto ADD PRIMARY KEY (PRODUTO);

INSERT INTO tbcliente (CPF,NOME,ENDERECO1,ENDERECO2,BAIRRO,CIDADE,ESTADO,CEP,DATA_NASCIMENTO,IDADE,SEXO,LIMITE_CREDITO,VOLUME_COMPRA,PRIMEIRA_COMPRA) VALUES ('19290992743','Fernando Cavalcante','R. Dois de Fevereiro','','Água Santa','Rio de Janeiro','RJ','22000000','2000-02-12',18,'M',100000,200000,1);

INSERT INTO tbcliente (CPF,NOME,ENDERECO1,ENDERECO2,BAIRRO,CIDADE,ESTADO,CEP,DATA_NASCIMENTO,IDADE,SEXO,LIMITE_CREDITO,VOLUME_COMPRA,PRIMEIRA_COMPRA) VALUES ('2600586709','César Teixeira','Rua Conde de Bonfim','','Tijuca','Rio de Janeiro','RJ','22020001','2000-03-12',18,'M',120000,220000,0);

INSERT INTO tbcliente (CPF,NOME,ENDERECO1,ENDERECO2,BAIRRO,CIDADE,ESTADO,CEP,DATA_NASCIMENTO,IDADE,SEXO,LIMITE_CREDITO,VOLUME_COMPRA,PRIMEIRA_COMPRA) VALUES ('95939180787','Fábio Carvalho','R. dos Jacarandás da Península','','Barra da Tijuca','Rio de Janeiro','RJ','22002020','1992-01-05',16,'M',90000,180000,1);

INSERT INTO tbcliente (CPF,NOME,ENDERECO1,ENDERECO2,BAIRRO,CIDADE,ESTADO,CEP,DATA_NASCIMENTO,IDADE,SEXO,LIMITE_CREDITO,VOLUME_COMPRA,PRIMEIRA_COMPRA) VALUES ('9283760794','Edson Meilelles','R. Pinto de Azevedo','','Cidade Nova','Rio de Janeiro','RJ','22002002','1995-10-07',22,'M',150000,250000,1);

INSERT INTO tbcliente (CPF,NOME,ENDERECO1,ENDERECO2,BAIRRO,CIDADE,ESTADO,CEP,DATA_NASCIMENTO,IDADE,SEXO,LIMITE_CREDITO,VOLUME_COMPRA,PRIMEIRA_COMPRA) VALUES ('7771579779','Marcelo Mattos','R. Eduardo Luís Lopes','','Brás','São Paulo','SP','88202912','1992-03-25',25,'M',120000,200000,1);

INSERT INTO tbcliente (CPF,NOME,ENDERECO1,ENDERECO2,BAIRRO,CIDADE,ESTADO,CEP,DATA_NASCIMENTO,IDADE,SEXO,LIMITE_CREDITO,VOLUME_COMPRA,PRIMEIRA_COMPRA) VALUES ('5576228758','Petra Oliveira','R. Benício de Abreu','','Lapa','São Paulo','SP','88192029','1995-11-14',22,'F',70000,160000,1);

INSERT INTO tbcliente (CPF,NOME,ENDERECO1,ENDERECO2,BAIRRO,CIDADE,ESTADO,CEP,DATA_NASCIMENTO,IDADE,SEXO,LIMITE_CREDITO,VOLUME_COMPRA,PRIMEIRA_COMPRA) VALUES ('8502682733','Valdeci da Silva','R. Srg. Édison de Oliveira','','Jardins','São Paulo','SP','82122020','1995-10-07',22,'M',110000,190000,0);

INSERT INTO tbcliente (CPF,NOME,ENDERECO1,ENDERECO2,BAIRRO,CIDADE,ESTADO,CEP,DATA_NASCIMENTO,IDADE,SEXO,LIMITE_CREDITO,VOLUME_COMPRA,PRIMEIRA_COMPRA) VALUES ('1471156710','Érica Carvalho','R. Iriquitia','','Jardins','São Paulo','SP','80012212','1990-09-01',27,'F',170000,245000,0);

INSERT INTO tbcliente (CPF,NOME,ENDERECO1,ENDERECO2,BAIRRO,CIDADE,ESTADO,CEP,DATA_NASCIMENTO,IDADE,SEXO,LIMITE_CREDITO,VOLUME_COMPRA,PRIMEIRA_COMPRA) VALUES ('3623344710','Marcos Nougeuira','Av. Pastor Martin Luther King Junior','','Inhauma','Rio de Janeiro','RJ','22002012','1995-01-13',23,'M',110000,220000,1);

INSERT INTO tbcliente (CPF,NOME,ENDERECO1,ENDERECO2,BAIRRO,CIDADE,ESTADO,CEP,DATA_NASCIMENTO,IDADE,SEXO,LIMITE_CREDITO,VOLUME_COMPRA,PRIMEIRA_COMPRA) VALUES ('50534475787','Abel Silva ','Rua Humaitá','','Humaitá','Rio de Janeiro','RJ','22000212','1995-09-11',22,'M',170000,260000,0);

INSERT INTO tbcliente (CPF,NOME,ENDERECO1,ENDERECO2,BAIRRO,CIDADE,ESTADO,CEP,DATA_NASCIMENTO,IDADE,SEXO,LIMITE_CREDITO,VOLUME_COMPRA,PRIMEIRA_COMPRA) VALUES ('5840119709','Gabriel Araujo','R. Manuel de Oliveira','','Santo Amaro','São Paulo','SP','80010221','1985-03-16',32,'M',140000,210000,1);

INSERT INTO tbcliente (CPF,NOME,ENDERECO1,ENDERECO2,BAIRRO,CIDADE,ESTADO,CEP,DATA_NASCIMENTO,IDADE,SEXO,LIMITE_CREDITO,VOLUME_COMPRA,PRIMEIRA_COMPRA) VALUES ('94387575700','Walber Lontra','R. Cel. Almeida','','Piedade','Rio de Janeiro','RJ','22000201','1989-06-20',28,'M',60000,120000,1);

INSERT INTO tbcliente (CPF,NOME,ENDERECO1,ENDERECO2,BAIRRO,CIDADE,ESTADO,CEP,DATA_NASCIMENTO,IDADE,SEXO,LIMITE_CREDITO,VOLUME_COMPRA,PRIMEIRA_COMPRA) VALUES ('8719655770','Carlos Eduardo','Av. Gen. Guedes da Fontoura','','Jardins','São Paulo','SP','81192002','1983-12-20',34,'M',200000,240000,0);

INSERT INTO tbcliente (CPF,NOME,ENDERECO1,ENDERECO2,BAIRRO,CIDADE,ESTADO,CEP,DATA_NASCIMENTO,IDADE,SEXO,LIMITE_CREDITO,VOLUME_COMPRA,PRIMEIRA_COMPRA) VALUES ('5648641702','Paulo César Mattos','Rua Hélio Beltrão','','Tijuca','Rio de Janeiro','RJ','21002020','1991-08-30',26,'M',120000,220000,0);

INSERT INTO tbcliente (CPF,NOME,ENDERECO1,ENDERECO2,BAIRRO,CIDADE,ESTADO,CEP,DATA_NASCIMENTO,IDADE,SEXO,LIMITE_CREDITO,VOLUME_COMPRA,PRIMEIRA_COMPRA) VALUES ('492472718','Eduardo Jorge','R. Volta Grande','','Tijuca','Rio de Janeiro','RJ','22012002','1994-07-19',23,'M',75000,95000,1);

INSERT INTO tbproduto (PRODUTO, NOME, EMBALAGEM, TAMANHO, SABOR, PRECO_LISTA) VALUES ('1040107','Light - 350 ml - Melância','Lata','350 ml','Melância',4.555);

INSERT INTO tbproduto (PRODUTO, NOME, EMBALAGEM, TAMANHO, SABOR, PRECO_LISTA) VALUES ('1037797','Clean - 2 Litros - Laranja','PET','2 Litros','Laranja',16.008);

INSERT INTO tbproduto (PRODUTO, NOME, EMBALAGEM, TAMANHO, SABOR, PRECO_LISTA) VALUES ('1000889','Sabor da Montanha - 700 ml - Uva','Garrafa','700 ml','Uva',6.309);

INSERT INTO tbproduto (PRODUTO, NOME, EMBALAGEM, TAMANHO, SABOR, PRECO_LISTA) VALUES ('1004327','Videira do Campo - 1,5 Litros - Melância','PET','1,5 Litros','Melância',19.51);

INSERT INTO tbproduto (PRODUTO, NOME, EMBALAGEM, TAMANHO, SABOR, PRECO_LISTA) VALUES ('1088126','Linha Citros - 1 Litro - Limão','PET','1 Litro','Limão',7.004);

INSERT INTO tbproduto (PRODUTO, NOME, EMBALAGEM, TAMANHO, SABOR, PRECO_LISTA) VALUES ('544931','Frescor do Verão - 350 ml - Limão','Lata','350 ml','Limão',2.4595);

INSERT INTO tbproduto (PRODUTO, NOME, EMBALAGEM, TAMANHO, SABOR, PRECO_LISTA) VALUES ('1078680','Frescor do Verão - 470 ml - Manga','Garrafa','470 ml','Manga',5.1795);

INSERT INTO tbproduto (PRODUTO, NOME, EMBALAGEM, TAMANHO, SABOR, PRECO_LISTA) VALUES ('1042712','Linha Citros - 700 ml - Limão','Garrafa','700 ml','Limão',4.904);

INSERT INTO tbproduto (PRODUTO, NOME, EMBALAGEM, TAMANHO, SABOR, PRECO_LISTA) VALUES ('788975','Pedaços de Frutas - 1,5 Litros - Maça','PET','1,5 Litros','Maça',18.011);

INSERT INTO tbproduto (PRODUTO, NOME, EMBALAGEM, TAMANHO, SABOR, PRECO_LISTA) VALUES ('1002767','Videira do Campo - 700 ml - Cereja/Maça','Garrafa','700 ml','Cereja/Maça',8.41);

INSERT INTO tbproduto (PRODUTO, NOME, EMBALAGEM, TAMANHO, SABOR, PRECO_LISTA) VALUES ('231776','Festival de Sabores - 700 ml - Açai','Garrafa','700 ml','Açai',13.312);

INSERT INTO tbproduto (PRODUTO, NOME, EMBALAGEM, TAMANHO, SABOR, PRECO_LISTA) VALUES ('479745','Clean - 470 ml - Laranja','Garrafa','470 ml','Laranja',3.768);

INSERT INTO tbproduto (PRODUTO, NOME, EMBALAGEM, TAMANHO, SABOR, PRECO_LISTA) VALUES ('1051518','Frescor do Verão - 470 ml - Limão','Garrafa','470 ml','Limão',3.2995);

INSERT INTO tbproduto (PRODUTO, NOME, EMBALAGEM, TAMANHO, SABOR, PRECO_LISTA) VALUES ('1101035','Linha Refrescante - 1 Litro - Morango/Limão','PET','1 Litro','Morango/Limão',9.0105);

INSERT INTO tbproduto (PRODUTO, NOME, EMBALAGEM, TAMANHO, SABOR, PRECO_LISTA) VALUES ('229900','Pedaços de Frutas - 350 ml - Maça','Lata','350 ml','Maça',4.211);

INSERT INTO tbproduto (PRODUTO, NOME, EMBALAGEM, TAMANHO, SABOR, PRECO_LISTA) VALUES ('1086543','Linha Refrescante - 1 Litro - Manga','PET','1 Litro','Manga',11.0105);

INSERT INTO tbproduto (PRODUTO, NOME, EMBALAGEM, TAMANHO, SABOR, PRECO_LISTA) VALUES ('695594','Festival de Sabores - 1,5 Litros - Açai','PET','1,5 Litros','Açai',28.512);

INSERT INTO tbproduto (PRODUTO, NOME, EMBALAGEM, TAMANHO, SABOR, PRECO_LISTA) VALUES ('838819','Clean - 1,5 Litros - Laranja','PET','1,5 Litros','Laranja',12.008);

INSERT INTO tbproduto (PRODUTO, NOME, EMBALAGEM, TAMANHO, SABOR, PRECO_LISTA) VALUES ('326779','Linha Refrescante - 1,5 Litros - Manga','PET','1,5 Litros','Manga',16.5105);

INSERT INTO tbproduto (PRODUTO, NOME, EMBALAGEM, TAMANHO, SABOR, PRECO_LISTA) VALUES ('520380','Pedaços de Frutas - 1 Litro - Maça','PET','1 Litro','Maça',12.011);

INSERT INTO tbproduto (PRODUTO, NOME, EMBALAGEM, TAMANHO, SABOR, PRECO_LISTA) VALUES ('1041119','Linha Citros - 700 ml - Lima/Limão','Garrafa','700 ml','Lima/Limão',4.904);

INSERT INTO tbproduto (PRODUTO, NOME, EMBALAGEM, TAMANHO, SABOR, PRECO_LISTA) VALUES ('243083','Festival de Sabores - 1,5 Litros - Maracujá','PET','1,5 Litros','Maracujá',10.512);

INSERT INTO tbproduto (PRODUTO, NOME, EMBALAGEM, TAMANHO, SABOR, PRECO_LISTA) VALUES ('394479','Sabor da Montanha - 700 ml - Cereja','Garrafa','700 ml','Cereja',8.409);

INSERT INTO tbproduto (PRODUTO, NOME, EMBALAGEM, TAMANHO, SABOR, PRECO_LISTA) VALUES ('746596','Light - 1,5 Litros - Melância','PET','1,5 Litros','Melância',19.505);

INSERT INTO tbproduto (PRODUTO, NOME, EMBALAGEM, TAMANHO, SABOR, PRECO_LISTA) VALUES ('773912','Clean - 1 Litro - Laranja','PET','1 Litro','Laranja',8.008);

INSERT INTO tbproduto (PRODUTO, NOME, EMBALAGEM, TAMANHO, SABOR, PRECO_LISTA) VALUES ('826490','Linha Refrescante - 700 ml - Morango/Limão','Garrafa','700 ml','Morango/Limão',6.3105);

INSERT INTO tbproduto (PRODUTO, NOME, EMBALAGEM, TAMANHO, SABOR, PRECO_LISTA) VALUES ('723457','Festival de Sabores - 700 ml - Maracujá','Garrafa','700 ml','Maracujá',4.912);

INSERT INTO tbproduto (PRODUTO, NOME, EMBALAGEM, TAMANHO, SABOR, PRECO_LISTA) VALUES ('812829','Clean - 350 ml - Laranja','Lata','350 ml','Laranja',2.808);

INSERT INTO tbproduto (PRODUTO, NOME, EMBALAGEM, TAMANHO, SABOR, PRECO_LISTA) VALUES ('290478','Videira do Campo - 350 ml - Melância','Lata','350 ml','Melância',4.56);

INSERT INTO tbproduto (PRODUTO, NOME, EMBALAGEM, TAMANHO, SABOR, PRECO_LISTA) VALUES ('783663','Sabor da Montanha - 700 ml - Morango','Garrafa','700 ml','Morango',7.709);

INSERT INTO tbproduto (PRODUTO, NOME, EMBALAGEM, TAMANHO, SABOR, PRECO_LISTA) VALUES ('235653','Frescor do Verão - 350 ml - Manga','Lata','350 ml','Manga',3.8595);

INSERT INTO tbproduto (PRODUTO, NOME, EMBALAGEM, TAMANHO, SABOR, PRECO_LISTA) VALUES ('1002334','Linha Citros - 1 Litro - Lima/Limão','PET','1 Litro','Lima/Limão',7.004);

INSERT INTO tbproduto (PRODUTO, NOME, EMBALAGEM, TAMANHO, SABOR, PRECO_LISTA) VALUES ('1013793','Videira do Campo - 2 Litros - Cereja/Maça','PET','2 Litros','Cereja/Maça',24.01);

INSERT INTO tbproduto (PRODUTO, NOME, EMBALAGEM, TAMANHO, SABOR, PRECO_LISTA) VALUES ('1096818','Linha Refrescante - 700 ml - Manga','Garrafa','700 ml','Manga',7.7105);

INSERT INTO tbproduto (PRODUTO, NOME, EMBALAGEM, TAMANHO, SABOR, PRECO_LISTA) VALUES ('1022450','Festival de Sabores - 2 Litros - Açai','PET','2 Litros','Açai',38.012);
```

# 3) Verifique o conteúdo das tabelas de produtos e clientes digitando:

```
SELECT * FROM tbproduto;

SELECT * FROM tbcliente;
```

# 4) Crie um novo script. Vamos fazer algumas consultas a base.

# 5) Digite:

```
SELECT * FROM tbcliente;

SELECT CPF, NOME, ENDERECO1, ENDERECO2, BAIRRO, CIDADE, ESTADO, CEP,
DATA_NASCIMENTO, IDADE, SEXO, LIMITE_CREDITO, VOLUME_COMPRA, PRIMEIRA_COMPRA
FROM tbcliente;
```

# 

Note que os dois comandos retornam a mesma coisa. Podemos usar o * para selecionar todos os campos ou discriminar um por um.

1. **Podemos selecionar alguns campos apenas:**

`SELECT CPF, NOME FROM tbcliente;`

## 7) Também é possível limitar a saída de registros:

`SELECT CPF, NOME FROM tbcliente LIMIT 5;`

### 8) Ou também criar um Label (Chamamos de Alias) para cada campo:

`SELECT CPF AS CPF_CLIENTE, NOME AS NOME_CLIENTE FROM tbcliente;`

# 9) Os registros podem ser filtrados usando o mesmo tipo de cláusula WHERE usada no UPDATE e DELETE.

`SELECT * FROM tbproduto WHERE PRODUTO = '544931';`

# 10) Mas não é somente pela chave primária que podemos filtrar as consultas.

```
SELECT * FROM tbcliente WHERE CIDADE = 'Rio de Janeiro';

SELECT * FROM tbproduto WHERE SABOR = 'Cítricos';
```

# 11) Inclusive este tipo de filtro WHERE pode ser usado no UPDATE e DELETE. Digite o comando abaixo de UPDATE para fazer uma alteração em diversos registros ao mesmo tempo.

`UPDATE tbproduto SET SABOR = 'Cítricos' WHERE SABOR = 'Limão';`

# 12) Podemos fazer consultas usando condições baseadas em números (Decimais ou inteiros). Crie um novo script e vamos a alguns exemplos:

`SELECT * FROM tbcliente WHERE IDADE = 22;`

Aqui vemos uma igualdade.

1. Mas podemos usar sinal de maior, menor, maior ou igual, menor ou igual. Olhe alguns exemplos:

```
SELECT * FROM tbcliente WHERE IDADE > 22;

SELECT * FROM tbcliente WHERE IDADE < 22;

SELECT * FROM tbcliente WHERE IDADE <= 22;
```

# 14) Temos o sinal de diferente que é expresso como <>. Veja abaixo:

`SELECT * FROM tbcliente WHERE IDADE <> 22;`

# 15) As condições de maior, menor, maior ou igual, menor ou igual, diferente podem ser aplicado a textos. O critério será a ordem alfabética.

```
SELECT * FROM tbcliente WHERE NOME >= 'Fernando Cavalcante';

SELECT * FROM tbcliente WHERE NOME <> 'Fernando Cavalcante';
```

# 16) As condições de maior, menor, maior ou igual, menor ou igual, igual e diferente não se aplica muito bem a campos FLOAT.

```
SELECT * FROM tbproduto WHERE PRECO_LISTA > 16.008;

SELECT * FROM tbproduto WHERE PRECO_LISTA < 16.008;

SELECT * FROM tbproduto WHERE PRECO_LISTA <> 16.008;
```

## 17) O comando BETWEEN pode ser aplicado.

`SELECT * FROM tbproduto WHERE PRECO_LISTA BETWEEN 16.007 AND 16.009;`

# 18) Podemos usar como filtro datas. veja alguns exemplos:

```
SELECT * FROM tbcliente WHERE DATA_NASCIMENTO = '1995-01-13';

SELECT * FROM tbcliente WHERE DATA_NASCIMENTO > '1995-01-13';

SELECT * FROM tbcliente WHERE DATA_NASCIMENTO <= '1995-01-13';
```

# 19) Existem algumas funções de data que podem ser usadas como filtros.

```
SELECT * FROM tbcliente WHERE YEAR(DATA_NASCIMENTO) = 1995;

SELECT * FROM tbcliente WHERE MONTH(DATA_NASCIMENTO) = 10;
```

# 20) Podemos usar filtros compostos usando, entre cada teste, os comandos AND ou OR. Veja abaixo alguns exemplos que podem ser testados no Workbench.

```
SELECT * FROM tbproduto WHERE PRECO_LISTA BETWEEN 16.007 AND 16.009;

SELECT * FROM tbproduto WHERE PRECO_LISTA >= 16.007;

SELECT * FROM tbproduto WHERE PRECO_LISTA <= 16.009;

SELECT * FROM tbproduto WHERE PRECO_LISTA >= 16.007 AND PRECO_LISTA <= 16.009;

SELECT * FROM tbcliente WHERE IDADE >= 18 AND IDADE <= 22;

SELECT * FROM tbcliente WHERE IDADE >= 18 AND IDADE <= 22 AND SEXO = 'M';

SELECT * FROM tbcliente WHERE CIDADE = 'Rio de Janeiro' OR BAIRRO = 'Jardins';

SELECT * FROM tbcliente WHERE (IDADE >= 18 AND IDADE <= 22 AND SEXO = 'M') OR (cidade = 'Rio de Janeiro' OR BAIRRO = 'Jardins');
```

# **About Queries and Subqueries**

A **query** is an operation that retrieves data from one or more tables or views. In this reference, a top-level `SELECT` statement is called a **query**, and a query nested within another SQL statement is called a **subquery**.

This section describes some types of queries and subqueries and how to use them. The top level of the syntax is shown in this chapter. Please refer to [SELECT](https://docs.oracle.com/cd/B19306_01/server.102/b14200/statements_10002.htm#i2065646) for the full syntax of all the clauses and the semantics of this statement.

***select*::=**

![https://docs.oracle.com/cd/B19306_01/server.102/b14200/img/select.gif](https://docs.oracle.com/cd/B19306_01/server.102/b14200/img/select.gif)

[Description of the illustration select.gif](https://docs.oracle.com/cd/B19306_01/server.102/b14200/img_text/select.htm)

***subquery*::=**

![https://docs.oracle.com/cd/B19306_01/server.102/b14200/img/subquery.gif](https://docs.oracle.com/cd/B19306_01/server.102/b14200/img/subquery.gif)

# **Creating Simple Queries**

The list of expressions that appears after the `SELECT` keyword and before the `FROM` clause is called the **select list**. Within the select list, you specify one or more columns in the set of rows you want Oracle Database to return from one or more tables, views, or materialized views. The number of columns, as well as their datatype and length, are determined by the elements of the select list.

If two or more tables have some column names in common, then you must qualify column names with names of tables. Otherwise, fully qualified column names are optional. However, it is always a good idea to qualify table and column references explicitly. Oracle often does less work with fully qualified table and column names.

You can use a column alias, *`c_alias`*, to label the immediately preceding expression in the select list so that the column is displayed with a new heading. The alias effectively renames the select list item for the duration of the query. The alias can be used in the `ORDER` `BY` clause, but not other clauses in the query.

You can use comments in a `SELECT` statement to pass instructions, or **hints**, to the Oracle Database optimizer. The optimizer uses hints to choose an execution plan for the statement. Please refer to ["Using Hints"](https://docs.oracle.com/cd/B19306_01/server.102/b14200/sql_elements006.htm#i35922) and *[Oracle Database Performance Tuning Guide](https://docs.oracle.com/cd/B19306_01/server.102/b14211/toc.htm)* for more information on hints.

`CREATE TABLE tbcliente;`

```
CREATE TABLE tbcliente
(CPF VARCHAR(11),
```

```
CREATE TABLE tbcliente"
( CPF VARCHAR (11) ,
NOME VARCHAR (100) ,
ENDERECO1 VARCHAR (150) ,
ENDERECO2 VARCHAR (150) ,
BAIRRO VARCHAR (50) ,
CIDADE VARCHAR (50) ,
ESTADO VARCHAR (2) ,
CEP VARCHAR (8) ,
IDADE SMALLINT,
SEXO VARCHAR (1) ,
LIMITE_CREDITO FLOAT ,
VOLUME_COMPRA FLOAT ,
PRIMEIRA_COMPRA BIT (1)
```

```
CREATE TABLE TABELA_DE_VENDEDORES (
    MATRICULA varchar(5),
    NOME varchar(100),
    PERCENTUAL_COMISSAO float
);
```

```
CREATE TABLE tbcliente2
( CPF VARCHAR (11) ,
NOME VARCHAR (100) ,
ENDERECO1 VARCHAR (150) ,
ENDERECO2 VARCHAR (150) ,
BAIRRO VARCHAR (50) ,
CIDADE VARCHAR (50) ,
ESTADO VARCHAR (2) ,
CEP VARCHAR (8) ,
IDADE SMALLINT,
SEXO VARCHAR (1) ,
LIMITE_CREDITO FLOAT ,
VOLUME_COMPRA FLOAT ,
PRIMEIRA_COMPRA BIT (1));
```

`DROP TABLE tbcliente3;`

```
CREATE TABLE TABELA_DE_VENDEDORES2 (
        MATRICULA varchar(5),
        NOME varchar(100),
        PERCENTUAL_COMISSAO float
);
```

```
USE sucos;

INSERT INTO tbproduto (
PRODUTO,
NOME,
EMBALAGEM,
TAMANHO,
SABOR,
PRECO_LISTA)
```

```
INSERT INTO tbproduto (
PRODUTO,
NOME,
EMBALAGEM,
TAMANHO,
SABOR,
PRECO_LISTA) VALUES (
'1040107', 'Light - 350 ml - Melancia', 'Lata', '350 ml', 'Melancia', 4.56);
```

```
Matrícula: 00233
Nome: João Geraldo da Fonseca
Comissão: 10%
```

```
INSERT INTO TABELA_DE_VENDEDORES
(MATRICULA, NOME, PERCENTUAL_COMISSAO)
VALUES
('00233', 'João Geraldo da Fonseca', 0.10);
```

# Criando uma view no Oracle SQL

Uma *View* funciona de forma semelhante a uma tabela. É utilizada em comandos **SELECT**, **INSERT**, **UPDATE** e **DELETE**, para recuperação e manipulação de dados (com restrições), porém, não armazena esses dados.

Este objeto tem suas linhas e colunas calculadas dinamicamente através de um **SELECT** pré-estabelecido, cada vez que solicitamos. Apenas a sua definição é armazenada no dicionário de dados.

Podemos dizer que se trata de uma tabela virtual, pois não possui linhas próprias, mas sim as obtém em tempo de execução e as disponibiliza em memória para acesso por uma *query*.

# **Como criar Views**

`Create [or replace] view  as
[with read only];`

Exemplo: Criando e visualizando as informações de uma view:

`Create view estoque as select codprod, descricao from produtos
where pmedio < 1000;`

# **Alterando uma View**

O comando **REPLACE** recria uma *view* já existente. Deve ser utilizado para alterar uma visão existente sem necessidade de apagá-la. É utilizado também para atribuir nova permissão e privilégios.

`Create or replace view estoque as select codprod, descricao, pvenda preço
from produtos where pmedio < 1000;`

# **Visualizando uma View**

`Select * from estoque;
Desc estoque;`

# **Excluindo uma View**

O comando **DROP VIEW** exclui uma *view* do dicionário de dados. Nenhum efeito ocorrerá sobre as tabelas referenciadas, bastando para isso ter apenas o privilégio **DROP VIEW** ou **DBA**.

`Drop view estoque;`

# **A Cláusula WITH CHECK OPTION**

Através da cláusula **WITH CHECK OPTION**, podemos garantir que os dados inseridos ou atualizados numa tabela através de uma *view*, poderão ser visualizados através da própria *view* com esta opção.

Exemplo:

`Create or replace view estoque as select codprod, descricao, pvenda preço
from produtos where pmedio < 1000 with check option estoque;`

# **A Cláusula WITH READ ONLY**

Através da cláusula **WITH READ ONLY** podemos impedir operações de DML sobre a *view*, restringindo desta forma a *view* apenas à leitura. A cláusula **WITH READ ONLY** indica que apenas a operação de consulta (**SELECT**) será permitida na *view* e, desse modo, operações de atualização, inserção e exclusão não serão permitidas.

Exemplo:

`Create or replace view estoque as select codprod, descricao, pvenda preço
from produtos where pmedio < 1000 with read only;`

A *view* está protegida para operações DML, portanto em qualquer tentativa de comandos referentes a DML (inserção, atualização e deleção) ocorrerão erros.

# **Checando as Views no Dicionário de Dados**

O Dicionário de Dados do Oracle nos permite checar as *views* criadas, bastando para isso usar o comando:

`Desc User_Views;`

Já sabemos incluir e alterar registros na tabela, agora vamos aprender como apagar. Para analisar os elementos da tabela, vamos selecionar somente o comando `SELECT * FROM tbproduto;`, será exibida a seguinte tabela:

[Untitled](https://www.notion.so/cb6d25242b18425ead93820c401761bb)

Vamos escolher o produto `1078680` para excluir. Abrindo um novo arquivo de edição para escrever o comando, insira `USE sucos;` e na próxima linha `DELETE FROM tbproduto`, mas, note que não há uma condição do que apagar, se rodarmos assim o comando vai excluir todos os registros da tabela. Por isso, é necessário incluir uma condição, igual fizemos no *UPDATE* utilizando a cláusula *WHERE*.

> Cuidado para não confundir DROP e DELETE. O DROP é utilizado para apagar objetos do MySQL, como, banco de dados, tabelas, índices e chave primária. Já o DELETE é para excluir registros armazenados em uma tabela do banco de dados.
>
