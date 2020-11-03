# postgres_pgAdmin4_docker

# para criar a estrutura do banco foi usado a  application.properties da aplicação Springboot cities-api

# 1 execute o docker-compose para criar as imagens Docker e o volume para o banco

  * $ docker-compose up -d 
  
# 2 acesse o bash do container do banco com o comando:  

  * docker exec -it ID_container /bin/bash
  
# 3 Configurar segurança para o psql pedir senha:
  
  * 3.1-root@facde61a16d6:/# apt update  && apt install nano 
  * 3.2-root@facde61a16d6:/# su - postgres
  * 3.3-postgres=# show hba_file;
  * 3.5-root@facde61a16d6:/# nano /var/lib/postgresql/data/pg_hba.conf
  * 3.6-troque a configuração de segurança do user postgres para md5
  * 3.7-root@facde61a16d6:/# su - postgres 
  * 3.8-postgres@IdeaPad-G485:~$ psql
  * 3.9-digite a senha que esta no arquivo docker-compose.yaml
  * 3.9.1-postgres=#
  
# 4 mudar para o banco a ser usado:

   * \c nome-banco  
   
# 5 coloque os arquivos.sql dentro do volume backups que foi criado e execute :
  
   *  nome-banco=# \i /var/lib/postgresql/backups/arquivo.sql 
   
# 6 confirmando se as tabelas foram preenchidas.

   * nome-banco=# select * from nome_tabela;   