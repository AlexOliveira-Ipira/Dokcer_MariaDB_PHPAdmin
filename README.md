<H1> Rodando mariaDB com phpmyadmin </h1>

<h2> Registrar no site do Docker HUB </h2>


 <h1> As imagens utilizadas nesse projeto foram baixadas desses reposit[orios</h1>
    <h2> Imagem mariaDB </h2>
            https://hub.docker.com/_/mariadb
        
<img src=./img/mariadockerhub.png>
    <h2> Imagem phpmyadmin </h2>
            https://hub.docker.com/_/phpmyadmin?tab=description

<img src=./img/phpmyadmindockerhub.png>


<h2> Criando Volume para guardar os dados do banco </h2>

    - Comando para cirar o volume
        docker volume create base_mariaDB

<img src=./img/volume.png>


<h2> Criando rede </h2>

    - Comando para criar a rede
        docker network create NetMariaDB

<img src=./img/network.png>


<h2> Rodando os containers </h2>

<h1> Container MariaDB </h1>

    - Comando para rodar o container

    docker container run -p 127.0.0.1:3306:3306 \
    -v "base_mariaDB:/dados" \
    --name mariaDB -e MARIADB_ROOT_PASSWORD=senha123 \
    --network NetMariaDB -d mariadb:10.6.4

<img src=./img/DockerMariaDB.png>

<h1> Container phpmyadmin </h1>
    
    - Comando para rodar o container

    docker container run --name phpadmin -d --link mariaDB:db -p 8080:80 -e MYSQL_PASSWORD=senha123 --network NetMariaDB phpmyadmin

<img src=./img/ContainerPHPMYadmin.png>

<h1> Rodando o PHPMyadmim </h1>
<p> Para rodar o PHPMyadmi deve ser feito aesso em http://localhost:8080 utilizar o </p>
<p> usuário root e a senha a definina ao rodar o container, no cso do exemplo a </p>
<p> senha é senha123 </p>

<h1> Imagens da tela de Abertuda do PHPMyadmin </h1>

<img src=./img/LogimPHP.png>

<h1> Painel PHPMyadmin </h1>

<img src=./img/Dashboard.png>