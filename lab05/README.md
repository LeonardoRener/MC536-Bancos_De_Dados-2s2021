# Modelo para Apresentação do Lab05 - Marcadores e Taxonomia em Cypher

Estrutura de pastas:

~~~
├── README.md  <- arquivo apresentando a tarefa
~~~

# Aluno
* `201270`: `<Leonardo Rener de Oliveira>`

## Tarefa de Cypher sobre Marcadores e Taxonomia

## Tarefa 1

Escreva em Cypher uma consulta que retorne os marcadores da categoria `Serviços`, sem considerar as categorias subordinadas.

### Resolução
~~~cypher
MATCH (m:Marcador) - [:Pertence] - >(c:Categoria)
WHERE c.id='Serviços'
RETURN m
~~~

## Tarefa 2

Escreva em Cypher uma consulta que retorne os marcadores da categoria `Serviços`, considerando as categorias subordinadas.

### Resolução
~~~cypher
MATCH (m: Marcador) - [:Pertence] -> (c1: Categoria), (c2: Categoria {id: "Serviços"})
WHERE (c1) - [:Superior *] -> (c2) OR c1.id = 'Serviços'
RETURN m
~~~
