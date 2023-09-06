###### Conceitos e melhores práticas com banco de dados PostgreSQL
# Configuração
> Arquivo postgresql.conf
> Arquivo pg_hba.conf
> Arquivo pg_ident.conf
> Comandos administrativos

## Arquivo postgresql.conf
### Definição
Arquivo onde estão definidas e armazenadas todas as configurações do servidor PostgreSQL.
Alguns parâmetros só podem ser alterados com uma reinicialização do banco de dados. 
A view pg_settings, acessada por dentro do banco de dados, guarda todas as configurações atuais.

### postgresql.conf
**Ao acessar a view pg_settings, é possível visualizar todas as configurações atuais:**
SELECT name, setting
FROM pg_settings;
**Ou é possível usar o comando:**
SHOW |parâmetro|;

### Localização do arquivo postgresql.conf
Por padrão, encontra-se dentro do diretório **PGDATA** definido no momento da inicialização do cluster de banco de dados.
No sistema operacional Ubunto, se o PostgreSQL foi instalado a partir do repositório oficial, o local do arquivo **postgresql.conf** será diferente do diretório de dados.
> /etc/postgresql/|versão|/|nome do cluster|/ ostgresql.conf

### Configuração de conexão
- **LISTEN_ADDRESSES**
  Endereço(s) TCP/IP das interfaces que o servidor PostgreSQL vai escutar/liberar conexões.
- **PORT**
  A porta TCP que o servidor PostgreSQL vai ouvir. O padrão é 5432.
- **MAX_CONNECTIONS**
  Número máximo de conexões simultâneas no servidor PostgreSQL.
- **SUPERUSER_RESERVED_CONNECTIONS**
  Número de conexoes (slots) reservadas para conexões ao banco de dados de super usuários.

### Configuração de autenticação
- **AUTHENTICATION_TIMEOUT**
  Tempo máximo em segundos para o cliente conseguir uma conexão com o servidor.
- **PASSWORD_ENCRYPTION** 
  Algoritmo de criptografia das senhas dos novos usuários criados no banco de dados.
- **SSL**
  Habilita a conexão criptografada por SSL (Somente se o PostgreSQL foi compilado com suporte SSL)

### Configurações de memória
- **SHARED_BUFFERS**
  Tamanho da memória para operações de agrupamento e ordenação (ORDER BY, DISTINCT, MERGE JOINS).
- **WORK_MEM**
  Tamanho da memória para operações de agrupamento e ordenação (ORDERBY, DISTINCT, MERGE JOINS).
- **MAINTENANCE_WORK_MEM**
  Tamanho da memória para operações como VACUUM, INDEX, ALTER TABLE.
  
## Arquivo pg_hba.conf
### Definição 
Arquivo responsável pelo controle de autenticação dos usuários no servidor PostgreSQL.

### Métodos de autenticação
- TRUST (conexão sem requisição de senha)
- REJECT (rejeitar conexões)
- MD5 (criptografia md5)
- PASSWORD (senha sem criptografia)
- GSS (generic security service application program interface)
- SSPI (security support provider interface - somente para Windows)
- KRB5 (kerberos V5)
- IDENT (utiliza o usuário do sistema operacional do cliente via ident server)
- PEER (utiliza o usuário do sistema operacional do cliente)
- LDAP (ldap server)
- RADIUS (radius server)
- CERT (autenticação via certificado ssl do cliente)
- PAM (pluggable authentication modules. O usuário precisa estar no bd)

## Arquivo pg_ident.conf
### Definição 
Arquivo responsável por mapear os usuários do sistema operacional com os usuários do banco de dados.
Localizado no diretório de dados **PGDATA** de sua instalação.
A opção **ident** deve ser utilizada no arquivo **pg_hba.conf**.

## Comandos administrativos
###### Ubunto
- **pg_lsclusters**
  Lista todos os clusters PostgreSQL
- **pg_createcluster<version><cluster name>**
  Cria um novo cluster PostgreSQL
- **pg_dropcluster <version> <cluster>**
  Apaga um cluster PostgreSQL
- **pg_ctlcluster <version> <cluster> <action>**
  Start, Stop, Status, Restart de clusters PostgreSQL

###### CentOS:
- **systemctl <action> <cluster>**
  - **systemctl start postgresql-11**
  Inicia o cluster PostgreSQL
  - **systemctl status postgresql-11**
  Mostra o status do cluster PostgreSQL
  - **systemctl stop postgresql-11**
  Para o cluster PostgreSQL
  - **systemctl restart postgresql-11**
  Restarta o cluster PostgreSQL

###### Windows:
Na área de serviços dentro do gerenciador de tarefas terá todos os comandos só que na interface gráfica.

### Binários do PostgreSQL:
- createdb
- createuser
- dropdb
- dropuser
- initdb
- pg_clt
- pg_basebackup
- pg_dump / pg_dumpall
- pg_restore
- psql
- reindexdb
- vacuumdb

## Arquitetura/Hierarquia
### Cluster
Coleção de bancos de dados que compartilham as mesmas configurações (arquivos de configuração) do PostgreSQL e do sistema operacional (porta, listen_addresses, e etc).

### Banco de dados (database)
Conjunto de schemas com seus objetos/relações (tabelas, funções, views, etc)

