---
{"dg-publish":true,"permalink":"/04-cadernos/2023-03-21-postgre-sql/","tags":["🧠️/📝️/🌿️"],"created":"2023-03-21T15:48:45.107-03:00","updated":"2023-05-17T15:04:18.733-03:00"}
---







# 🌿️ 2023-03-21 - 📝️ PostgreSQL
<small>21/03/2023</small>

```toc
```
<br>

***



## ← [[❝ 2023-03-21 - 🎒 PostgreSQL - comandos DML e DDL]]

![Pasted image 20230321102652.png|undefined](/img/user/XX%20-%20Anexos/Pasted%20image%2020230321102652.png)
Servidor → bancos de dados → tabelas/entidades → informações

![Pasted image 20230321103410.png|undefined](/img/user/XX%20-%20Anexos/Pasted%20image%2020230321103410.png)

```sql
CREATE SCHEMA 
```
- Conhecemos o conceito de modelagem de dados;
- Conhecemos sobre schemas no PostgreSQL que nos ajudam a organizar nossas tabelas;
- Conversamos sobre análise de requisitos e sobre modelos utilizados neste processo;

![Pasted image 20230321131201.png|undefined](/img/user/XX%20-%20Anexos/Pasted%20image%2020230321131201.png)

`CREATE DATABASE name OWNER foo_bar`

Alternativa correta
`CREATE DATABASE name WITH OWNER = foo_bar`

CREATE TABLE — define a new table
[PostgreSQL: Documentation: 15: CREATE TABLE](https://www.postgresql.org/docs/current/sql-createtable.html)

ALTER TABLE name RENAME TO novo nome
ALTER TABLE nome da tabela RENAME [COLUMN] TO novo nome da coluna
ALTER TABLE teste RENAME coluna1 TO primeira_coluna

![Pasted image 20230321135523.png|undefined](/img/user/XX%20-%20Anexos/Pasted%20image%2020230321135523.png)
DDL - data definition language, ou linguagem de definição de dados.

DML, que é data manipulation language, ou linguagem de manipulação dos dados

***
- Desmembramos a criação de um banco de dados e aprofundamos esse conhecimento;
- Falamos sobre os detalhes ao criar uma tabela;
- Conhecemos o ALTER TABLE para alterar a estrutura de uma tabela;
- Vimos a diferença entre comandos DDL e DML.
***

`insert into select`

```sql
	CREATE SCHEMA teste; 
	
	CREATE TABLE teste.cursos_programacao(
		id_curso INTEGER PRIMARY KEY,
		nome_curso VARCHAR(255) NOT NULL);
		
	INSERT INTO teste.cursos_programacao
	SELECT academico.curso.id,
			academico.curso.nome
	FROM academico.curso
	WHERE categoria_id = 2;
```
COPY FROM algo e COPY TO algo

`COPY pessoa FROM '/pasta/arquivo.csv';`
***
- Entendemos as particularidades da representação de tipos e uso de aspas em SQL;
- Conhecemos o comando INSERT SELECT que realiza inserções a partir de uma consulta;
- Falamos sobre importação e exportação de dados em arquivos CSV.
***
UPDATE
```sql
UPDATE academico.curso SET nome = ‘i’; WHERE id = ; -- alterações com condicionante
```


```sql
UPDATE teste.cursos_programacao SET nome_curso = nome
FROM academico.curso WHERE teste.cursos_programacao.id_curso = academico.curso.id
AND academico.curso.id < 10;

```

```sql
DELETE FROM curso
      USING categoria
      WHERE categoria.id = curso.categoria_id
        AND categoria.nome = 'Teste';

```

**Transações**

```sql
START TRANSACTION; 
BEGIN;
ROLLBACK; -- reverte os codigos depois do begin

BEGIN;
COMMIT; -- salva as alterações que os codigos causaram 

-- nunca pode deixar transação aberta
```
https://www.postgresql.org/docs/current/tutorial-transactions.html
***
- Conhecemos a sintaxe do UPDATE FROM, que atualiza uma tabela baseando-se em dados de uma consulta;
- Vimos os perigos de uma alteração ou remoção incorreta (sem WHERE, por exemplo);
- Aprendemos a trabalhar com transações;
- Vimos como confirmar ou cancelar uma transação.
***
**Sequencias** 

```sql
CREATE SEQUENCE eu_criei;  -- sequencia CURRVAL E NEXTVAL
SELECT CURRVAL('eu_criei');

CREATE TEMPORARY TABLE 	AUTO(       -- temporary table
	id INTEGER PRIMARY KEY DEFAULT NEXTVAL('eu_criei'),
	nome VARCHAR(30) NOT NULL
);

INSERT INTO auto (nome) VALUES ('Marta Safaneta');
INSERT INTO auto (id, nome) VALUES (2, 'Marta Safaneta');
INSERT INTO auto (nome) VALUES ('Marta Safaneta');

INSERT INTO 

SELECT * FROM auto;

```
**CREATE TYPE - ENUM**

```sql
-- criar tipo enum
CREATE TYPE CLASSIFICACAO AS ENUM ('LIVRE', '12_ANOS', '14_ANOS', '16_ANOS', '18_ANOS')
CREATE TEMPORARY TABLE filme(
	id SERIAL PRIMARY KEY,
	nome VARCHAR(255) NOT NULL,
	classificacao CLASSIFICACAO
);

INSERT INTO filme (nome, classificacao) VALUES ('1 filme qqr', 'teste')
INSERT INTO filme (nome, classificacao) VALUES ('1 filme qqr', 'LIVRE')

SELECT * FROM filme
```
[PostgreSQL: Documentation: 15: CREATE TYPE](https://www.postgresql.org/docs/current/sql-createtype.html)
***
- Conhecemos as SEQUENCEs do PostgreSQL;
- Aprendemos o que é uma ENUM;
- Aprendemos a criar um tipo personalizado no banco de dados;
- Conversamos sobre como bancos de dados são utilizados na vida real.

*** 

<small>==2023-04-02== <br> ← [[❝ 2023-03-21 - 🎒 PostgreSQL - desenvolva com PL pgSQL]]</small>


**Funções**
```sql
CREATE FUNCTION primeira_funcao() RETURNS INTEGER AS '
	SELECT(5-3)*2

' LANGUAGE SQL

SELECT primeira_funcao() AS numero;
```

```sql
CREATE FUNCTION soma_dois_numeros(numero_1 INTEGER, numero_2 INTEGER) RETURNS INTEGER AS '
	SELECT numero_1 + numero_2;
' LANGUAGE SQL;

SELECT soma_dois_numeros(3, 17)

DROP FUNCTION soma_dois_numeros; -- drop do mesmo jeito
  
  -- mesma função sem definir nomes abaixo
CREATE FUNCTION soma_dois_numeros(INTEGER, INTEGER) RETURNS INTEGER AS '
	SELECT $1 + $2;                
' LANGUAGE SQL;

SELECT soma_dois_numeros(3, 17)
```

```sql
CREATE TABLE a (nome varchar) RETURNS void AS $$
	INSERT INTO a (nome) VALUES('Patricia');
$$ LANGUAGE SQL;

SELECT cria_a('Vinicius Dias');
```

`CREATE OR REPLACE`
Os tipos (tanto dos parâmetros quanto do retorno) não podem ser diferentes


O que define o valor que será retornado em uma função?
A primeira linha da última query é retornada

**Procedure**

Uma Procedure no PostgreSQL é exatamente igual a uma função tendo como diferença o fato de que não retorna nenhum valor.

CALL nome_do_procedure

[PostgreSQL: Documentation: 15: 38.4. User-Defined Procedures](https://www.postgresql.org/docs/current/xproc.html)
***
- Começamos falando sobre o propósito de programar diretamente no banco de dados;
- Conhecemos o conceito de funções no PostgreSQL;
- Entendemos sobre tipos em
- Parâmetros
- Retornos de funções
- Falamos sobre como retornar valores em funções escritas em SQL.
***
**Parametros compostos**

```sql
CREATE TABLE instrutor (
	id SERIAL PRIMARY KEY,
	nome VARCHAR(255) NOT NULL,
	salario DECIMAL(10, 2)
);

INSERT INTO instrutor (nome, salario) VALUES ('Vinicius Dias', 100);

CREATE FUNCTION dobro_do_salario(instrutor) RETURNS DECIMAL AS $$ 
	SELECT $1.salario * 2 AS dobro;
$$ LANGUAGE SQL;

SELECT nome, dobro_do_salario(instrutor.*) FROM instrutor;

CREATE OR REPLACE FUNCTION cria_instrutor_falso() RETURNS instrutor AS $$
	SELECT 22, 'Nome falso', 200::DECIMAL;
$$ LANGUAGE SQL;

SELECT * FROM cria_instrutor_falso();


```

```sql
CREATE FUNCTION instrutores_bem_pagos(valor_salario DECIMAL) RETURNS SETOF instrutor AS $$
	SELECT * FROM instrutor WHERE salario > valor_salario;
$$ LANGUAGE SQL;

SELECT * FROM instrutores_bem_pagos(300);
```


```sql
CREATE FUNCTION soma_e_produto (numero_1 INTEGER, numero_2 INTEGER, OUT soma INTEGER, OUT produto INTEGER) AS $$
	SELECT numero_1 + numero_2 AS soma, numero_1 * numero_2 AS produto;
$$ LANGUAGE SQL

SELECT * FROM soma_e_produto(3, 3);
--- as duas funções dão o mesmo resultado
CREATE TYPE dois_valores AS (soma INTEGER, produto INTEGER);
CREATE FUNCTION soma_e_produto (numero_1 INTEGER, numero_2 INTEGER) RETURNS dois_valores AS $$
	SELECT numero_1 + numero_2 AS soma, numero_1 * numero_2 AS produto;
$$ LANGUAGE SQL

SELECT * FROM soma_e_produto(3, 3);
```
***
- Entendemos que podemos trabalhar com tipos "compostos";
- Vimos que podemos representar tipos compostos de diversas formas
- Definindo seu valor como o registro de uma tabela
- Como um tipo personalizado do PostgreSQL
- Com variáveis de saída
- Entendemos como retornar mais de um dado por vez em nossas funções através do SETOF
- Conhecemos um dos possíveis usos para o tipo RECORD.
***
## PLpgSQL

```sql
CREATE OR REPLACE FUNCTION primeira_pl() RETURNS INTEGER AS $$
	BEGIN
		-- varios comandos SQL
		RETURN 1;
	END
$$ LANGUAGE plpgsql;

SELECT primeira_pl();
```

***

```sql
CREATE OR REPLACE FUNCTION primeira_pl() RETURNS INTEGER AS $$
	DECLARE -- variaveis
		primeira_variavel INTEGER DEFAULT 3;         -- ou := 3
	BEGIN
		primeira_variavel := primeira_variavel * 2;
		RETURN 1;
	END
$$ LANGUAGE plpgsql;

SELECT primeira_pl();
```

Vimos que há 3 formas de definir o valor padrão de uma variável ao declará-la:

1 - DEFAULT
 2 - `:=`
 3 - =
Agora um detalhe importante de se citar é que no corpo da função, ou seja, entre os blocos BEGIN e END nós não podemos utilizar o DEFAULT para atribuir (ou modificar) o valor de uma variável. Apenas as 2 últimas opções são possíveis.


```sql
CREATE OR REPLACE FUNCTION primeira_pl() RETURNS INTEGER AS $$
	DECLARE 
		primeira_variavel INTEGER DEFAULT 3;
	BEGIN
		primeira_variavel := primeira_variavel * 2;
		
		DECLARE 
			primeira_variavel INTEGER;
		BEGIN
			primeira_variavel := 7;
		END
		RETURN primeira_variavel;
	END
$$ LANGUAGE plpgsql;

SELECT primeira_pl();
```

Declaro um novo bloco aqui, nesse novo bloco o que estou fazendo é declarar outra variável que tem um nome primeira_variavel, mas está em outro lugar da memória, é outra variável.

[01:55] Essa outra variável defino que o valor dela vai ser 7. Quando encerro esse bloco, essa variável deixa de existir, é como se ela nunca tivesse existido, porque ela foi declarada aqui dentro. O que vou acessar e o que vou retornar é essa variável definida aqui em cima, que tem valor 6.

[02:12] Por isso recebemos o valor 6. Agora, se eu fizer esse bloco sem o declare, ele vai ter acesso à variável que foi definida no bloco pai. Aqui sim ele vai conseguir alterar a variável original. Nesse caso, se eu substituir a função e executar, tenho um retorno sendo 7, ou seja, os blocos filhos têm acesso a todas as variáveis dos blocos pais, dos blocos acima.

[02:44] Só que se eu definir uma variável que já existe, ela vai ser outra, vai ser uma variável nova sem nenhuma relação com a variável de cima, com a variável do bloco pai.
***
- Entendemos as limitações do SQL quando se trata de programação;
- Conhecemos a linguagem PLpgSQL, que é uma linguagem de Programação Procedural criada pelo PostgreSQL como uma extensão ao SQL;
- Aprendemos sobre a estrutura básica de criação de uma função usando PLpgSQL;
- Aprendemos a definir variáveis;
- Entendemos o conceito de blocos e escopos usando PLpgSQL.

***

```sql
CREATE OR REPLACE FUNCTION cria_instrutor_falso() RETURNS instrutor AS $$
	DECLARE 
		retorno instrutor;
	BEGIN
		SELECT 22, 'Nome falso', 200::DECIMAL INTO retorno;
		RETURN returno;
	END;
$$ LANGUAGE plpgsql;

SELECT id, salario FROM cria_instrutor_falso();

```

```sql
CREATE FUNCTION instrutores_bem_pagos(valor_salario DECIMAL) RETURNS SETOF instrutor AS $$
	BEGIN
		RETURN QUERY SELECT * FROM instrutor WHERE salario > valor_salario;
	END;
$$ LANGUAGE plpgSQL;

SELECT * FROM instrutores_bem_pagos(300);
```

### if, else, elseif

```sql
CREATE FUNCTION salario_ok(instrutor instrutor) RETURNS VARCHAR AS $$ 
	BEGIN
		IF instrutor.salario > 200 THEN
			RETURN 'Salário está ok';
		ELSE
			RETURN 'Salário pode aumentar';
		END IF;
	END;
$$ LANGUAGE plpgsql;

SELECT nome, salario_ok(instrutor) FROM instrutor;
```

```sql
DROP FUNCTION salario_ok

CREATE FUNCTION salario_ok(instrutor instrutor) RETURNS VARCHAR AS $$ 
	BEGIN
		IF instrutor.salario > 300 THEN
			RETURN 'Salário está ok';
		ELSEIF instrutor.salario = 300 THEN
			RETURN 'Salário pode aumentar';
		ELSE 
			RETURN 'Aumento de salário necessário!';
		END IF;
	END;
$$ LANGUAGE plpgsql;

SELECT nome, salario_ok(instrutor) FROM instrutor;
```

### Case

```sql
CREATE FUNCTION salario_ok(instrutor instrutor) RETURNS VARCHAR AS $$ 
	BEGIN
		CASE instrutor.salario
		WHEN 100 THEN
			RETURN 'Salário muito baixo';
		WHEN 200 THEN
			RETURN 'Salário baixo';
		WHEN 300 THEN
			RETURN 'Salário okay';
		ELSE 
			RETURN 'Salário bom';
		END CASE;
	END;
$$ LANGUAGE plpgsql;

SELECT nome, salario_ok(instrutor) FROM instrutor;
```
***
O que aprendemos nessa aula:

- Vimos como retornar valores utilizando PLpgSQL;
- Aprendemos a tomar decisões em nossos códigos usando IF;
- Conseguimos controlar o fluxo de nossa aplicação com ELSEIF e ELSE;
- Aprendemos a deixar nosso código um pouco mais legível com CASE.
***
### Return next 

```sql
CREATE OR REPLACE FUNCTION tabuada(numero INTEGER) RETURNS SETOF INTEGER AS $$ 
	DECLARE
	BEGIN
		RETURN NEXT numero * 1;
		RETURN NEXT numero * 2;
		RETURN NEXT numero * 3;
		RETURN NEXT numero * 4;
		RETURN NEXT numero * 5;
		RETURN NEXT numero * 6;
		RETURN NEXT numero * 7;
		RETURN NEXT numero * 8;
		RETURN NEXT numero * 9;
		RETURN NEXT numero * 10;
	END;
$$ LANGUAGE plpgsql;

SELECT tabuada(2);
```

### Loop

```sql
CREATE OR REPLACE FUNCTION tabuada(numero INTEGER) RETURNS SETOF VARCHAR AS $$ 
	DECLARE
		multiplicador INTEGER DEFAULT 1;
	BEGIN
		LOOP
			RETURN NEXT numero || ' x ' || multiplicador || ' = ' || numero * multiplicador;
			multiplicador := multiplicador + 1;
			
			EXIT WHEN multiplicador = 10;
		END LOOP;
	END;
$$ LANGUAGE plpgsql;

SELECT tabuada(2);
```

Saindo do loop com while

```sql

CREATE OR REPLACE FUNCTION tabuada(numero INTEGER) RETURNS SETOF VARCHAR AS $$ 
	DECLARE
		multiplicador INTEGER DEFAULT 1;
	BEGIN
		WHILE multiplicador < 10 LOOP
			RETURN NEXT numero || ' x ' || multiplicador || ' = ' || numero * multiplicador;
			multiplicador := multiplicador + 1;
		END LOOP;
	END;
$$ LANGUAGE plpgsql;

```

### FOR

```sql
CREATE OR REPLACE FUNCTION tabuada(numero INTEGER) RETURNS SETOF VARCHAR AS $$ 
	BEGIN
		FOR multiplicador IN 1..9 LOOP
			RETURN NEXT numero || ' x ' || multiplicador || ' = ' || numero * multiplicador;
		END LOOP;
	END;
$$ LANGUAGE plpgsql;
```

```sql
CREATE FUNCTION instrutor_com_salario(OUT nome VARCHAR, OUT salario_ok VARCHAR) RETURNS SETOF record AS $$ 
	DECLARE 
		instrutor instrutor;
	BEGIN
		FOR instrutor IN SELECT * FROM instrutor LOOP
			nome := instrutor.nome;
			salario_ok = salario_ok(instrutor.id);
		
			RETURN NEXT;
		END LOOP;
		END;
$$ LANGUAGE plpgsql;

SELECT * FROM instrutor_com_salario();
```

Documentação de loops [PostgreSQL: Documentation: 15: 43.6. Control Structures](https://www.postgresql.org/docs/current/plpgsql-control-structures.html#PLPGSQL-CONTROL-STRUCTURES-LOOPS)
***
O que aprendemos nessa aula:

- Vimos mais uma forma de retornar valores através do RETURN NEXT;
- Entendemos a necessidade de realizar operações "repetidas" em determinadas funções;
- Aprendemos a usar a estrutura LOOP para repetir instruções;
- Usamos EXIT para não cairmos em um "loop infinito";
- Conhecemos a estrutura WHILE para facilitar a leitura do LOOP sem precisar do EXIT;
- Aprendemos a usar (e quando usar) o famoso FOR;
- Vimos como percorrer o resultado de uma query usando FOR IN.
***
```sql

CREATE FUNCTION cria_curso(nome_curso VARCHAR, nome_categoria VARCHAR) RETURNS void AS $$ 
	DECLARE
		id_categoria INTEGER;
	BEGIN
		SELECT id INTO id_categoria FROM categoria WHERE nome = nome_categoria;
		IF NOT FOUND THEN
			INSERT INTO categoria (nome) VALUES (nome_categoria) RETURNING id INTO id_categoria;
		END IF;
		INSERT INTO curso (nome, categoria_id) VALUES (nome_curso, id_categoria);
		
	END;
$$ LANGUAGE plpgsql;

SELECT cria_curso('Papel 1', 'Conrest papel');


SELECT * FROM categoria;
```

variável FOUND: Esta variável é definida automaticamente em toda função em PLpgSQL e começa como FALSE. Nesse link você confere em que situações ela será definida como TRUE: https://www.postgresql.org/docs/current/plpgsql-statements.html#PLPGSQL-STATEMENTS-DIAGNOSTICS

### Exemplo

```sql
CREATE TABLE log_instrutores (
	id SERIAL PRIMARY KEY,
	informacao VARCHAR(255),
	momento_criacao TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);

CREATE OR REPLACE FUNCTION cria_instrutor (nome_instrutor VARCHAR, salarios_instrutor DECIMAL) RETURNS void AS $$ 
	DECLARE
		id_instrutor_inserido INTEGER;
		media_salarial DECIMAL;
		instrutores_recebem_menos INTEGER DEFAULT 0;
		total_instrutores INTEGER DEFAULT 0;
		salario DECIMAL;
		percentual DECIMAL;
	BEGIN
		INSERT INTO instrutor (nome, salario) VALUES (nome_instrutor, salário_instrutor) RETURNING id INTO id_instrutor_inserido;
		SELECT AVG(instrutor.salario) INTO media_salarial FROM instrutor WHERE id <> id_instrutor_inserido;
		
		IF salario_instrutor > media_salarial THEN
			INSERT INTO log_instrutores (informacao) VALUES (nome_instrutor || ' recebe acima da média');
		END IF;
		
		FOR salario IN SELECT instrutor.salario FROM instrutor WHERE id <> id_instrutor_inserido LOOP
			total_instrutores := total_instrutores + 1;
			IF salario_instrutor > salario THEN
				instrutores_recebem_menos := instrutores_recebem_menos + 1;
			END IF;
		END LOOP;
		percentual = instrutores_recebem_menos::DECIMAL / total_instrutorres::DECIMAL * 100;
		INSERT INTO log_instrutores (informação)
			VALUES (nome_instrutor || ' recebe mais que ' || percentual || '% da grade de instrutores');
	END;
$$ LANGUAGE plpgsql;

SELECT * FROM log_instrutores;

SELECT cria_instrutor('Fulana', 1000)
```

Se nós tivermos uma string contendo uma query válida, podemos executar essa query através do comando EXECUTE da linguagem PLpgSQL.

Para ver exemplos e ler sobre mais detalhes, dá uma olhada aqui: https://www.postgresql.org/docs/current/plpgsql-statements.html#PLPGSQL-STATEMENTS-EXECUTING-DYN
***
O que aprendemos nessa aula:

- Criamos funções mais próximas da vida real;
- Aprendemos sobre a variável automaticamente criada em funções com PLpgSQL chamada FOUND;
- Conseguimos realizar logs de operações feitas no banco de dados;
- Aprendemos a realizar cálculos com conversões de tipos usando PLpgSQL.
***
<small>==2023-04-06== <br> [[❝ 2023-04-02 - 🎒 PostgreSQL - Triggers, transações, erros e cursores]]</small>

### Trigger Procedures
https://www.postgresql.org/docs/current/plpgsql-trigger.html

```sql 
CREATE OR REPLACE FUNCTION cria_instrutor () RETURNS TRIGGER AS $$ 
	DECLARE
		media_salarial DECIMAL;
		instrutores_recebem_menos INTEGER DEFAULT 0;
		total_instrutores INTEGER DEFAULT 0;
		salario DECIMAL;
		percentual DECIMAL;
	BEGIN
		SELECT AVG(instrutor.salario) INTO media_salarial FROM instrutor WHERE id <> NEW.id;
		
		IF NEW.salario > media_salarial THEN
			INSERT INTO log_instrutores (informacao) VALUES (NEW.nome || ' recebe acima da média');
		END IF;
		
		FOR salario IN SELECT instrutor.salario FROM instrutor WHERE id <> NEW.id LOOP
			total_instrutores := total_instrutores + 1;
			IF NEW.salario > salario THEN
				instrutores_recebem_menos := instrutores_recebem_menos + 1;
			END IF;
		END LOOP;
		percentual = instrutores_recebem_menos::DECIMAL / total_instrutores::DECIMAL * 100;
		INSERT INTO log_instrutores (informação)
			VALUES (NEW.nome || ' recebe mais que ' || percentual || '% da grade de instrutores');
		RETURN NEW;
	END;
$$ LANGUAGE plpgsql;

CREATE TRIGGER cria_log_instrutores AFTER INSERT ON instrutor
	FOR EACH ROW EXECUTE FUNCTION cria_instrutor ();

INSERT INTO instrutor (nome, salario) VALUES ('Fulana', 600);

DROP TRIGGER cria_log_instrutores ON instrutor;
```


**Particularidades do comando `CREATE TRIGGER`**
Existe a possibilidade da gente definir um trigger usando a sintaxe `EXECUTE PROCEDURE` ao invés de `EXECUTE FUNCTION`. Isso existe por razões históricas e não faz diferença nenhuma na prática.

> [!info]+ Particularidades sobre triggers
> `FOR EACH ROW`  
> executará a função uma vez para cada linha modificada
> `FOR EACH STATEMENT`
> executará a função apenas uma vez para cada instrução, independente do número de linhas modificadas
> as variáveis `OLD` e `NEW` não estarão definidas já que a execução não é por linha modificada

***
- Entendemos o conceito de eventos no banco de dados
- Aprendemos como criar um Trigger Procedure
- Definimos um Trigger que executa uma Trigger Procedure quando um evento ocorre
- Entendemos a fundo detalhes de triggers como `FOR EACH ROW | STATEMENT`, etc
- Vimos que há 2 sintaxes para iniciar uma transação: BEGIN e START TRANSACTION
- Entendemos que funções por si só já fazem parte de uma transação
- Aprendemos que erros cancelam as alterações de uma função
***
### Capturando erros

```sql
[ <<label>> ]
[ DECLARE
    declarations ]
BEGIN
    statements
EXCEPTION
    WHEN condition [ OR condition ... ] THEN
        handler_statements
    [ WHEN condition [ OR condition ... ] THEN
          handler_statements
      ... ]
END;
```

> [Appendix A](https://www.postgresql.org/docs/15/errcodes-appendix.html)
> Documentação: https://www.postgresql.org/docs/15/plpgsql-control-structures.html#PLPGSQL-ERROR-TRAPPING

### Levantando erros e mensagens → Rollback para função

```sql 
RAISE [ level ] 'format' [, expression [, ... ]] [ USING option = expression [, ... ] ];
RAISE [ level ] condition_name [ USING option = expression [, ... ] ];
RAISE [ level ] SQLSTATE 'sqlstate' [ USING option = expression [, ... ] ];
RAISE [ level ] USING option = expression [, ... ];
RAISE ;
```

> [!info]+ `level` → Severidade | Gravidade 
> padrão é `EXCEPTION`
> gera um erro e interrompe a execução (desde que não haja um bloco `EXCEPTION` para tratá-la)
> `DEBUG`, `LOG`, `INFO`, `NOTICE`, `WARNING`
> Documentação: https://www.postgresql.org/docs/15/plpgsql-errors-and-messages.html

#### Exemplo
```sql
CREATE OR REPLACE FUNCTION cria_instrutor () RETURNS TRIGGER AS $$ 
	DECLARE
		media_salarial DECIMAL;
		instrutores_recebem_menos INTEGER DEFAULT 0;
		total_instrutores INTEGER DEFAULT 0;
		salario DECIMAL;
		percentual DECIMAL;
	BEGIN
		SELECT AVG(instrutor.salario) INTO media_salarial FROM instrutor WHERE id <> NEW.id;
		IF NEW.salario > media_salarial THEN
			INSERT INTO log_instrutores (informacao) VALUES (NEW.nome || ' recebe acima da média');
		END IF;
		
		FOR salario IN SELECT instrutor.salario FROM instrutor WHERE id <> NEW.id LOOP
			total_instrutores := total_instrutores + 1;
			IF NEW.salario > salario THEN
				instrutores_recebem_menos := instrutores_recebem_menos + 1;
			END IF;
		END LOOP;
		percentual = instrutores_recebem_menos::DECIMAL / total_instrutores::DECIMAL * 100;
		INSERT INTO log_instrutores (informação, teste)
			VALUES (NEW.nome || ' recebe mais que ' || percentual || '% da grade de instrutores');
		RETURN NEW;
			EXECEPTION         -- excepção
			WHEN undefined_column THEN
			RAISE NOTICE 'Algo de errado não está certo';  -- mensagem que aparece para o usuario
			RAISE EXCEPTION 'Erro complicado de resolver';
			RETURN NEW;
	END;
$$ LANGUAGE plpgsql;

CREATE TRIGGER cria_log_instrutores AFTER INSERT ON instrutor
	FOR EACH ROW EXECUTE FUNCTION cria_instrutor ();
```


### `Assert`

```sql
CREATE OR REPLACE FUNCTION cria_instrutor () RETURNS TRIGGER AS $$ 
	DECLARE
		media_salarial DECIMAL;
		instrutores_recebem_menos INTEGER DEFAULT 0;
		total_instrutores INTEGER DEFAULT 0;
		salario DECIMAL;
		percentual DECIMAL;
	BEGIN
		SELECT AVG(instrutor.salario) INTO media_salarial FROM instrutor WHERE id <> NEW.id;
		IF NEW.salario > media_salarial THEN
			INSERT INTO log_instrutores (informacao) VALUES (NEW.nome || ' recebe acima da média');
		END IF;
		
		FOR salario IN SELECT instrutor.salario FROM instrutor WHERE id <> NEW.id LOOP
			total_instrutores := total_instrutores + 1;
			IF NEW.salario > salario THEN
				instrutores_recebem_menos := instrutores_recebem_menos + 1;
			END IF;
		END LOOP;
		percentual = instrutores_recebem_menos::DECIMAL / total_instrutores::DECIMAL * 100;
		ASSERT percentual < 100::DECIMAL, 'Instrutores novos não podem receber mais que os antigos';

		INSERT INTO log_instrutores (informação, teste)
			VALUES (NEW.nome || ' recebe mais que ' || percentual || '% da grade de instrutores');
		RETURN NEW;
			EXECEPTION         -- excepção
			WHEN undefined_column THEN
			RAISE NOTICE 'Algo de errado não está certo';  -- mensagem que aparece para o usuario
			RAISE EXCEPTION 'Erro complicado de resolver';
			RETURN NEW;
	END;
$$ LANGUAGE plpgsql;

CREATE TRIGGER cria_log_instrutores BEFORE INSERT ON instrutor
	FOR EACH ROW EXECUTE FUNCTION cria_instrutor ();
```

### Depuração 

```sql
EXCEPTION
    WHEN OTHERS THEN     -- vê todos os erros
    --executa bloco de código
END;

-- ou

GET DIAGNOSTICS

-- ou chamar mensagens apresentando resultados como
RAISE NOTICE 'Salário inserido: % Salário existente: %', NEW.salario, salario;
-- declara em ordem as variaveis que substituem os %
```
***
- Aprendemos o que são os erros (ou exceções) do PostgreSQL
- Aprendemos a gerar erros e mensagens com o RAISE
- Aprendemos a usar o ASSERT que verifica condições e levanta exceções
- Entendemos que o RAISE pode ser usado no processo de depuração
***
### Cursores

```sql
DECLARE
    curs1 refcursor;
    curs2 CURSOR FOR SELECT * FROM tenk1;
    curs3 CURSOR (key integer) FOR SELECT * FROM tenk1 WHERE unique1 = key;
```

> [!info]+ Documentação
> https://www.postgresql.org/docs/15/plpgsql-cursors.html

#### _unbound cursor_

```sql
CREATE FUNCTION instrutores_internos (id_instrutor INTEGER) RETURNS refcursor AS $$ 
	DECLARE
		cursor_salarios refcursor; -- não ligado a nenhuma query
	BEGIN
		OPEN cursor_salarios FOR SELECT instrutor.salario  -- aberto posteriormente 
								   FROM instrutor 
								  WHERE id <> id_instrutor 
								  	AND salario > 0;      -- query
	END;
$$ LANGUAGE plpgsql;
```

#### _bound cursor_

```sql
CREATE FUNCTION instrutores_internos (id_instrutor INTEGER) RETURNS refcursor AS $$ 
	DECLARE
		cursor_salarios CURSOR FOR SELECT instrutor.salario   
								   FROM instrutor 
								  WHERE id <> id_instrutor 
								  	AND salario > 0;    -- ligado a uma query desde o começo
	BEGIN
		OPEN cursor_salarios;        -- preciso abrir para atualizar
	END;
$$ LANGUAGE plpgsql;
```

#### Exemplo

```sql
DROP TABLE instrutor

CREATE TABLE instrutor(
id SERIAL PRIMARY KEY,
nome VARCHAR (255) NOT NULL,
salario DECIMAL (10, 2));


INSERT INTO instrutor (nome, salario) VALUES ('Trator', 400);
INSERT INTO instrutor (nome, salario) VALUES ('Bagagem', 500);
INSERT INTO instrutor (nome, salario) VALUES ('Tosco', 600);
INSERT INTO instrutor (nome, salario) VALUES ('Meia', 600);


SELECT * FROM log_instrutores

CREATE FUNCTION instrutores_internos (id_instrutor INTEGER) RETURNS refcursor AS $$ 
	DECLARE
		cursor_salarios refcursor;
		salario DECIMAL;
	BEGIN
		OPEN cursor_salarios FOR SELECT instrutor.salario 
								   FROM instrutor 
								  WHERE id <> id_instrutor 
								  	AND salario > 0;
		RETURN cursor_salario;
	END;
$$ LANGUAGE plpgsql;
```

#### `FETCH` e `MOVE`

`FETCH` além de mover o “ponteiro” do cursor, devolve o valor após mover. O `MOVE` apenas move o “ponteiro” sem devolver nenhum valor

>[!info]+ Documentação 
>[https://www.postgresql.org/docs/current/plpgsql-cursors.html#PLPGSQL-CURSOR-USING](https://www.postgresql.org/docs/current/plpgsql-cursors.html#PLPGSQL-CURSOR-USING)
***
-   Entendemos o propósito de usar cursores, para poupar uso de memória
-   Vimos como abrir cursores, sendo eles _bound_ ou _unbound_
-   Vimos como manipular cursores com `FETCH` e `MOVE`
-   Usamos cursores na prática em um `LOOP`
***
### Exemplo de código até agora!

```sql
DROP TABLE instrutor

CREATE TABLE instrutor(      -- cria tabela instrutor
id SERIAL PRIMARY KEY, 
nome VARCHAR (255) NOT NULL,
salario DECIMAL (10, 2));


INSERT INTO instrutor (nome, salario) VALUES ('Trator', 400);   -- adiciona valores
INSERT INTO instrutor (nome, salario) VALUES ('Bagagem', 500);
INSERT INTO instrutor (nome, salario) VALUES ('Tosco', 600);
INSERT INTO instrutor (nome, salario) VALUES ('Meia', 600);
INSERT INTO instrutor (nome, salario) VALUES ('Marta', 200);

CREATE OR REPLACE FUNCTION instrutores_internos (id_instrutor INTEGER) RETURNS refcursor AS $$     -- cursor
	DECLARE
		cursor_salarios refcursor; -- unbound
		salario DECIMAL;
	BEGIN
		OPEN cursor_salarios FOR SELECT instrutor.salario -- abrir cursor
								   FROM instrutor 
								  WHERE id <> id_instrutor 
								  	AND instrutor.salario > 0;
		RETURN cursor_salarios;
	END;
$$ LANGUAGE plpgsql;
```

```sql 
CREATE OR REPLACE FUNCTION cria_instrutor () RETURNS TRIGGER AS $$  
	DECLARE
		media_salarial DECIMAL;
		instrutores_recebem_menos INTEGER DEFAULT 0;
		total_instrutores INTEGER DEFAULT 0;
		salario DECIMAL;
		percentual DECIMAL;
		cursor_salarios refcursor;
	BEGIN
		SELECT AVG(instrutor.salario) INTO media_salarial FROM instrutor WHERE id <> NEW.id;
		IF NEW.salario > media_salarial THEN
			INSERT INTO log_instrutores (informacao) VALUES (NEW.nome || ' recebe acima da média');
		END IF;
		SELECT instrutores_internos(NEW.id) INTO cursor_salarios;
		LOOP
			FETCH cursor_salarios INTO salario;
			EXIT WHEN NOT FOUND;
			total_instrutores := total_instrutores + 1;
			IF NEW.salario > salario THEN
				instrutores_recebem_menos := instrutores_recebem_menos + 1;
			END IF;
		END LOOP;
		percentual = instrutores_recebem_menos::DECIMAL / total_instrutores::DECIMAL * 100;
		ASSERT percentual < 100::DECIMAL, 'Instrutores novos não podem receber mais que os antigos';
		INSERT INTO log_instrutores (informacao)
			VALUES (NEW.nome || ' recebe mais que ' || percentual || '% da grade de instrutores');
		RETURN NEW;
	END;
$$ LANGUAGE plpgsql; -- programação do relatorio log_instutores 

CREATE TRIGGER cria_log_instrutores AFTER INSERT ON instrutor
	FOR EACH ROW EXECUTE FUNCTION cria_instrutor (); -- cria o gatilho

INSERT INTO instrutor (nome, salario) VALUES ('Louie', 1200); -- isso adiciona ao valor e chama o gatilho, gerando entrada no log

SELECT * FROM log_instrutores -- ve o log criado 
```

### Blocos anônimos `DO`
Usado para gerar relatórios pontuais ou testar códigos antes de incorporá-los, neste caso ver o percentual do salario do 5º funcionário na média geral e ver se ele pode ganhar um hipotético aumento.

```sql
DO $$
	DECLARE
		cursor_salarios refcursor;
		salario DECIMAL;
		total_instrutores INTEGER DEFAULT 0;
		instrutores_recebem_menos INTEGER DEFAULT 0;
		percentual DECIMAL(5, 2);
	BEGIN
	
	SELECT instrutores_internos(5) INTO cursor_salarios;
		LOOP
			FETCH cursor_salarios INTO salario;
			EXIT WHEN NOT FOUND;
			total_instrutores := total_instrutores + 1;
			IF 600::DECIMAL > salario THEN
				instrutores_recebem_menos := instrutores_recebem_menos + 1;
			END IF;
		END LOOP;
		percentual = instrutores_recebem_menos::DECIMAL / total_instrutores::DECIMAL * 100;
		
		RAISE NOTICE 'Percentual: % %%', percentual;
	END;		
$$;
```

###  *Early return*
- [https://www.alura.com.br/artigos/quanto-mais-simples-melhor](https://www.alura.com.br/artigos/quanto-mais-simples-melhor)

***
-   Aprendemos a usar blocos anônimos com `DO`
-   Vimos que blocos anônimos possuem 2 principais propósitos
    -   Rodar um script pontual em PLpgSQL
    -   Preparar uma função para efetivamente criá-la no futuro
-   Entendemos que boas práticas de programação são muito importantes
-   Conhecemos algumas outras ferramentas além do PgAdmin como DataGrip e EMS
***

<small> ==2023-04-07== <br> ← [[❝ 2023-04-06 - 🎒 PostgreSQL - administração e otimização do banco]]</small>

## DBA: Database Administrator
### Responsabilidades
![Pasted image 20230406204453.png|undefined](/img/user/XX%20-%20Anexos/Pasted%20image%2020230406204453.png)

### Conexões com o banco
![Pasted image 20230406204920.png|undefined](/img/user/XX%20-%20Anexos/Pasted%20image%2020230406204920.png)
![Pasted image 20230406205000.png|undefined](/img/user/XX%20-%20Anexos/Pasted%20image%2020230406205000.png)
![Pasted image 20230406205016.png|undefined](/img/user/XX%20-%20Anexos/Pasted%20image%2020230406205016.png)
![Pasted image 20230406205036.png|undefined](/img/user/XX%20-%20Anexos/Pasted%20image%2020230406205036.png)

#### Datagrip
![Pasted image 20230406205150.png|undefined](/img/user/XX%20-%20Anexos/Pasted%20image%2020230406205150.png)
![Pasted image 20230406205754.png|undefined](/img/user/XX%20-%20Anexos/Pasted%20image%2020230406205754.png)

#### Cuidar do servidor e suas permissões

***
-   Entendemos qual o papel do DBA em uma empresa
-   Conhecemos o modelo cliente-servidor em que os bancos de dados funcionam
-   Vimos que o servidor pode receber conexões de diversos clientes
***
### Inicializando um espaço
![Pasted image 20230406210512.png|undefined](/img/user/XX%20-%20Anexos/Pasted%20image%2020230406210512.png)
![Pasted image 20230406210835.png|undefined](/img/user/XX%20-%20Anexos/Pasted%20image%2020230406210835.png)

### Subindo um servidor
> [!info]+ Documentação
> https://www.postgresql.org/docs/current/server-start.html

![Pasted image 20230406211800.png|undefined](/img/user/XX%20-%20Anexos/Pasted%20image%2020230406211800.png)
![Pasted image 20230406211843.png|undefined](/img/user/XX%20-%20Anexos/Pasted%20image%2020230406211843.png)

![Pasted image 20230406212001.png|undefined](/img/user/XX%20-%20Anexos/Pasted%20image%2020230406212001.png)
![Pasted image 20230406212035.png|undefined](/img/user/XX%20-%20Anexos/Pasted%20image%2020230406212035.png)

```
$ **`postgres -D /usr/local/pgsql/data >logfile 2>&1 &`**
```

#### Utilitário
```
pg_ctl start -l logfile
```

![Pasted image 20230406212501.png|undefined](/img/user/XX%20-%20Anexos/Pasted%20image%2020230406212501.png)

Através desse utilitários nós podemos fazer muita coisa com menos conhecimento sobre o sistema operacional, já que esse utilitário abstrai diversas complexidades para nós.

### Derrubando servidor

```
su postgres -c 'pg_ctl start -D /usr/local/pgsql/data -l serverlog'
```

> [!info]+ Documentação
> https://www.postgresql.org/docs/current/server-start.html

![Pasted image 20230406213615.png|undefined](/img/user/XX%20-%20Anexos/Pasted%20image%2020230406213615.png)

![Pasted image 20230406213648.png|undefined](/img/user/XX%20-%20Anexos/Pasted%20image%2020230406213648.png)

![Pasted image 20230406213702.png|undefined](/img/user/XX%20-%20Anexos/Pasted%20image%2020230406213702.png)

![Pasted image 20230406213720.png|undefined](/img/user/XX%20-%20Anexos/Pasted%20image%2020230406213720.png)

![Pasted image 20230406213737.png|undefined](/img/user/XX%20-%20Anexos/Pasted%20image%2020230406213737.png)

→ Desligar se servidor sob ataque, upgrade, etc

***
-   Entendemos o que é um cluster do PostgreSQL
-   Aprendemos a inicializar um cluster com o comando `initdb`
-   Entendemos como gerenciar o serviço do servidor PostgreSQL
-   Conhecemos o utilitário `pg_ctl`
***

### Hardware e nuvem

![Pasted image 20230406214700.png|undefined](/img/user/XX%20-%20Anexos/Pasted%20image%2020230406214700.png)

### Configurações postgreSQL

![Pasted image 20230406215700.png|undefined](/img/user/XX%20-%20Anexos/Pasted%20image%2020230406215700.png)

![Pasted image 20230406215816.png|undefined](/img/user/XX%20-%20Anexos/Pasted%20image%2020230406215816.png)

![Pasted image 20230406220001.png|undefined](/img/user/XX%20-%20Anexos/Pasted%20image%2020230406220001.png)

> [!info]+ Documentação
> [https://www.postgresql.org/docs/current/config-setting.html](https://www.postgresql.org/docs/current/config-setting.html)

***
-   Conversamos sobre Tuning do banco de dados
-   Entendemos que a escolha do hardware do servidor é importante, mas que serviços de nuvem abstraem esse detalhe para os DBAs
-   Conhecemos a pasta `data` do PostgreSQL onde encontramos o arquivo de configurações
-   Falamos sobre o papel do DBA na gestão do sistema operacional
***

### Uso de dados - Processos de manutenção

![Pasted image 20230406221128.png|undefined](/img/user/XX%20-%20Anexos/Pasted%20image%2020230406221128.png) → ![Pasted image 20230406221142.png|undefined](/img/user/XX%20-%20Anexos/Pasted%20image%2020230406221142.png) →  ![Pasted image 20230406221310.png|undefined](/img/user/XX%20-%20Anexos/Pasted%20image%2020230406221310.png) → ![Pasted image 20230406221324.png|undefined](/img/user/XX%20-%20Anexos/Pasted%20image%2020230406221324.png)

#### *Concurrency Control*

> [!info]+ Documentação
> https://www.postgresql.org/docs/15/mvcc-intro.html

#### VACUUM

> [!info]+ Documentação
> https://www.postgresql.org/docs/15/sql-vacuum.html

##### Exercicio para visualização de ocupação da memoria pelos registros e limpeza
```sql
DROP TABLE instrutor;
CREATE TABLE instrutor (
    id SERIAL PRIMARY KEY,
    nome VARCHAR(255) NOT NULL,
    salario DECIMAL(10, 2)
);
SELECT COUNT(*) FROM instrutor;
DO $$                                       -- insere 1000000 de registros
    DECLARE
    BEGIN
        FOR i IN 1..1000000 LOOP
            INSERT INTO instrutor (nome, salario) VALUES ('Instrutor(a) ' || i, random() * 1000 + 1);
        END LOOP;
    END;
$$;
UPDATE instrutor SET salario = salario * 2 WHERE id % 2 = 1; -- duplica salario de registros impares
DELETE FROM instrutor WHERE id % 2 = 0; -- deleta registros pares
VACUUM [ANALYSE | FULL | VERBOSE] instrutor;      -- varios tipos ver docs

SELECT relname, n_dead_tup FROM pg_stat_user_tables;    -- tuplas mortas (registro excluido)
SELECT pg_size_pretty(pg_relation_size('instrutor'));  -- tamanho que a tabela ta ocupando
```

O `VACUUM` apenas limpa as “tuplas mortas”. O `VACUUM FULL` também compacta os registros para poupar ainda mais espaço. O `VACUUM ANALYSE` além de limpar as “tuplas mortas”, também analisa as tabelas para atualizar as estatísticas do planejador de queries


#### `ANALYZE`
> [!info]+ Documentação
> https://www.postgresql.org/docs/15/sql-analyze.html

#### Reindexação de rotina → `REINDEX`
> [!info]+ Documentação
> https://www.postgresql.org/docs/15/routine-reindex.html

#### Rotação de LOGS

- compactar o pg.log e começar um novo.

> [!info]+ Documentação
> https://www.postgresql.org/docs/15/logfile-maintenance.html

***
-   Vimos que há processos de manutenção que podemos / devemos fazer no banco
-   Aprendemos como o PostgreSQL mantém alguns dados “inúteis” por questão de performance
-   Conhecemos o comando `VACUUM` para limpar espaço em disco
-   Vimos como reindexar as tabelas do banco com o comando `REINDEX`
***

### Processos de backup

![Pasted image 20230406234717.png|undefined](/img/user/XX%20-%20Anexos/Pasted%20image%2020230406234717.png)

![Pasted image 20230406235006.png|undefined](/img/user/XX%20-%20Anexos/Pasted%20image%2020230406235006.png)

![Pasted image 20230406235022.png|undefined](/img/user/XX%20-%20Anexos/Pasted%20image%2020230406235022.png)

![Pasted image 20230406235050.png|undefined](/img/user/XX%20-%20Anexos/Pasted%20image%2020230406235050.png)

![Pasted image 20230406235125.png|undefined](/img/user/XX%20-%20Anexos/Pasted%20image%2020230406235125.png)

![Pasted image 20230406235205.png|undefined](/img/user/XX%20-%20Anexos/Pasted%20image%2020230406235205.png)

![Pasted image 20230406235310.png|undefined](/img/user/XX%20-%20Anexos/Pasted%20image%2020230406235310.png)

![Pasted image 20230406235525.png|undefined](/img/user/XX%20-%20Anexos/Pasted%20image%2020230406235525.png)

![Pasted image 20230406235551.png|undefined](/img/user/XX%20-%20Anexos/Pasted%20image%2020230406235551.png)

![Pasted image 20230406235703.png|undefined](/img/user/XX%20-%20Anexos/Pasted%20image%2020230406235703.png)

![Pasted image 20230407000050.png|undefined](/img/user/XX%20-%20Anexos/Pasted%20image%2020230407000050.png)

![Pasted image 20230407000443.png|undefined](/img/user/XX%20-%20Anexos/Pasted%20image%2020230407000443.png)

![Pasted image 20230407000613.png|undefined](/img/user/XX%20-%20Anexos/Pasted%20image%2020230407000613.png)

***
-   Entendemos que há diferentes tipos de backup e conversamos sobre como fazê-los
-   Vimos que há 2 principais formas de fazer backups
    1.  Através da linha de comando (usando `pg_dump`)
    2.  Através de interfaces gráficas (por exemplo, usando o `PgAdmin`)
-   Aprendemos como restaurar backups realizados também de 2 formas diferentes
***

### `EXPLAIN`

``` sql
EXPLAIN SELECT * FROM instrutor WHERE salario > 1500;
```

![Pasted image 20230407124844.png|undefined](/img/user/XX%20-%20Anexos/Pasted%20image%2020230407124844.png)

> [!info]+ Documentação
> Uso: [https://www.postgresql.org/docs/current/using-explain.html](https://www.postgresql.org/docs/current/using-explain.html)
> Sintaxe: [https://www.postgresql.org/docs/current/sql-explain.html](https://www.postgresql.org/docs/current/sql-explain.html)


### `INDEX`

```sql
EXPLAIN SELECT * FROM instrutor WHERE salario > 1500;

CREATE INDEX idx_salario ON instrutor(salario);

DROP INDEX idx_salario

```

![Pasted image 20230407125417.png|undefined](/img/user/XX%20-%20Anexos/Pasted%20image%2020230407125417.png)

→ otimização porém com custos
→ aumentam a complexidade
→ usado só em alta complexidade

***
-   Conhecemos o conceito do planejador de queries (_Query Planner_) do PostgreSQL
-   Aprendemos que o comando `EXPLAIN` pode nos dar informações sobre como uma query é executada
-   Aprendemos o que são e como utilizar índices
-   Vimos que apesar de serem uma ferramenta muito poderosa, índices nem sempre são a solução
***

### pg_hba.conf

Configurações de permissão

> [!info]+ Documentação
> https://www.postgresql.org/docs/current/client-authentication.html


### Usuários | *Roles*

`CREATE ROLE Marta LOGIN`. 
`CREATE USER Marta`
`DROP ROLE Marta`
`ALTER ROLE`.

> [!info]+ Documentação
> https://www.postgresql.org/docs/15/database-roles.html
> `createuser`: [https://www.postgresql.org/docs/current/app-createuser.html](https://www.postgresql.org/docs/current/app-createuser.html)

#### Atributos de roles

→ criar banco, password, etc
→  `SUPERUSER` faz com que o `ROLE` ignore todos os atributos de restrição


> [!info]+ Documentação
> https://www.postgresql.org/docs/15/role-attributes.html

#### `REVOKE` 

> [!info]+ Documentação
> https://www.postgresql.org/docs/15/sql-revoke.html

#### `GRANT` 
> [!info]+ Documentação
> https://www.postgresql.org/docs/15/sql-grant.html

***
-   Vimos como permitir ou impedir o acesso ao servidor a partir de algum host
-   Conhecemos o arquivo `pg_hba.conf` que permite a configuração de acesso ao servidor baseado em hosts
-   Vimos que o PostgreSQL trabalha com um conceito de _ROLES_, que podem ser como usuários ou grupos
-   Aprendemos sobre os atributos dos _ROLES_
-   Entendemos que é possível dar ou retirar permissões específicas a _ROLES_
***