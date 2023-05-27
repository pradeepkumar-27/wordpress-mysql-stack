Wordpress MYSQL Application stack
===

Docker Compose
---
Deploy entire application stack with docker compose

    # docker-compose up -d
    
Delete entire application 
    
    # docker-compose down
    
Note: Command needs to be run where the "docker-compose.yml" file is present


Ad hoc commands :
---
    
    # docker network create -d bridge bridge-network --subnet=172.20.0.0/24

    # docker volume create mysql-db-volume

    # docker volume create wordpress-app-volume

    # docker container run -itd -e MYSQL_ROOT_PASSWORD=root \
    -e MYSQL_USER=wordpress -e MYSQL_PASSWORD=wordpress -e MYSQL_DATABASE=wordpress \
    -v mysql-db-volume:/var/lib/mysql --network bridge-network --name mysql-db mysql

    # docker container run -itd -e WORDPRESS_DB_HOST=mysql-db \
    -e WORDPRESS_DB_USER=wordpress -e WORDPRESS_DB_PASSWORD=wordpress -e WORDPRESS_DB_NAME=wordpress \
    -p 8080:80 --network bridge-network --name wordpress-app wordpress
    
___

Other resources :

[Docker installation on RedHat/Centos distros](https://www.linkedin.com/posts/pradeep-kumar-a68a9418b_docker-containerization-redhatenterpriselinux-activity-6848920877149642752-XmDf)