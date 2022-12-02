
# DOCKR STACK LARAVEL 9

A basic configuration to use laravel 9 with docker, php 8, nginx and postgres.

# COMANDS
1.- git clone the respository

2.- cd to the folder cloned

# DOCKER
- the docker folder contain all the files configuration to the stack.
    - PHP
    - NGINX
1.- docker-compose up  -d 
- will run the stack, build the src folder
- all the data will palced on data/ folder (volumes)

# DISPLAY
- on port 80 will be the app in laravel
- on port 81 will tbe the client of postgres (pgadmin)

BY Jose Diaz.