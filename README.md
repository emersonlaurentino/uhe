# UHE

Lista das usinas hidrelétricas integradas ao SIN coletada do [wikipedia](https://pt.wikipedia.org/wiki/Lista_de_usinas_hidrel%C3%A9tricas_do_Brasil).

O intuíto deste projeto é criar insights a partir do grafos utilizando o neo4j.

## Criando os nós

### Usina

```cypher
LOAD CSV WITH HEADERS FROM 'https://raw.githubusercontent.com/emersonlaurentino/uhe/main/usinas.csv' AS usina
CREATE (:Usina {nome: usina.nome, inicioOperacao: usina.inicioOperacao, potencia: usina.potencia })
```

#### Cria index para usina

```cypher
CREATE INDEX FOR (n:Usina) ON (n.nome)
```

### Bacias

```cypher
LOAD CSV WITH HEADERS FROM 'https://raw.githubusercontent.com/emersonlaurentino/uhe/main/bacias.csv' AS bacia
CREATE (:Bacia {nome: bacia.nome })
```

### Empresas
```cypher
LOAD CSV WITH HEADERS FROM 'https://raw.githubusercontent.com/emersonlaurentino/uhe/main/empresas.csv' AS empresa
CREATE (:Empresa {nome: empresa.nome })
```

### Rios
```cypher
LOAD CSV WITH HEADERS FROM 'https://raw.githubusercontent.com/emersonlaurentino/uhe/main/rios.csv' AS rio
CREATE (:Rio {nome: rio.nome })
```

### Estados
```cypher
LOAD CSV WITH HEADERS FROM 'https://raw.githubusercontent.com/emersonlaurentino/uhe/main/estados.csv' AS estado
CREATE (:Estado {nome: estado.nome })
```

### Sub Bacias
```cypher
LOAD CSV WITH HEADERS FROM 'https://raw.githubusercontent.com/emersonlaurentino/uhe/main/sub_bacias.csv' AS sub_bacia
CREATE (:SubBacia {nome: sub_bacia.nome })
```
