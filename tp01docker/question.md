1-1 For which reason is it better to run the container with a flag -e to give the environment variables rather than put them directly in the Dockerfile?

reponse : Pour des raisons de securite.

1-2 Why do we need a volume to be attached to our postgres container?

reponse : Pour stocker les données de la base de données de manière persistante.

1-3 Document your database container essentials: commands and Dockerfile.

faut mettre COPY docker-entrypoint-initdb.d/ /docker-entrypoint-initdb.d/
dans le docker file pour les scripts sql

docker run -d --name postgres-container --network app-network -p 5432:5432 -e POSTGRES_DB=db -e POSTGRES_USER=usr -e POSTGRES_PASSWORD=pwd -v $(pwd)/pgdata:/var/lib/postgresql/data postgres-db

on peut tester la base de données avec la commande suivante :
docker exec -it postgres-container psql -U usr -d db -c "SELECT \* FROM departments;"

1-4 Why do we need a multistage build? And explain each step of this dockerfile.

reponse :
