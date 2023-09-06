###### Conceitos e melhores práticas com banco de dados PostgreSQL
# Fundamentos de banco de dados

## Introdução
### O que são dados?
Valores brutos, fatos brutos, observações documentadas, registros soltos, que são recolhidos e armazenados sem sofrer qualquer tratamento.

### O que são informações?
Estruturação de dados, organização de dados. 
Conjunto de dados relacionados entre si que geram valor, que criam sentido aos dados.
Material do conhecimento.

## Modelo Relacional
Informações relacionais
(91) 90000-0000     -   Fulano 01
(91) 90000-0000     -   Fulano 02      
(91) 90000-0000     -   Fulano 03
(91) 90000-0000     -   Fulano 04
(91) 90000-0000     -   Fulano 05
    Telefones           Proprietários

### Tabelas
Conjuntos de dados dispostos em colunas e linhas referentes a um objetivo comum.
As colunas são consideradas como "campos da tabela", como atributos da tabela.
As linhas de uma tabela são chamadas também de tuplas, e é onde estão contidos os valores, os dados.

#### O que pode ser definido como tabelas?
- **Coisas tangíveis**
  - Elementos físicos (carro, produto, animal)
- **Funções**
  - Perfis de usuário, status de compra
- **Eventos ou ocorrências**
  - Produtos de um pedido, histórico de dados

#### Colunas importantes
- **Chave Primária / Primary Key / PK**
  - Conjunto de um ou mais campos que nunca se repetem. Identidade da tabela. São utilizados como índice de referência na criação de relacionamentos entre tabelas.
- **Chave Estrangeira / Foreign Key / FK**
  - Valor de referência a uma PK de outra tabela da mesma tabela para criar um relacionamento.

### Sistemas de gerenciamento de banco de dados
Ou Sistemas de gestão de base de dados.
Chamamos pela sigla SGBD.
Conjunto de programas ou softwares responsáveis pelo gerenciamento de um banco de dados.
Programas que facilitam a administração de um banco de dados.

## Introdução ao PostgreSQL
### O que é o PostgreSQL
Sistema de gerenciamento de bano de dados objeto relacional.
Teve início no Departamento de Ciência da Computação na Universidade da Califórnia em Berkeley em 1986.
SGBD Opensource.

### Principais características
- OpenSource
- Point in time recovery
- Liguagem procedural com suporte a várias linguagens de programação (perl, python, etc)
- Views, functions, procedures, triggers
- Consultas complexas e Common table expressions (CTE)
- Suporte a dados geográficos (PostGIS)
- Controle de concorrência multi-versão

### Instalação e documentação do PostgreSQL
[Site oficial](https://www.postgresql.org/)
[Download com instruções passo a passo](https://www.postgresql.org/download/)
[Documentação completa](https://www.postgresql.org/docs/manuals/)