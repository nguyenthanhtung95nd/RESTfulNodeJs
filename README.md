# Setting up your Environment

- Install nodejs via link  [link](https://nodejs.org/en/)
- Install expressjs

    ```Shell
        npm i express
    ```
- Install eslint
    ```Shell
        npm i eslint -D
    ```
- Install nodemon
    ```Shell
        npm i nodemon
    ```
    Add config into package.json file
    ```js
        "nodemonConfig": {
            "restartable": "rs",
            "ignore": [
            "node_modules/**/node_modules"
            ],
            "delay": "2500",
            "env": {
            "NODE_ENV": "development",
            "PORT": 4000
            }
        }
    ```
    ```js
        "scripts": {
            "lint": "eslint .",
            "start": "nodemon app.js",
            "test": "echo \"Error: no test specified\" && exit 1"
        },
    ```
- Install body-parser

    ```Shell
        npm i body-parser
    ```

# Setup MongoDb using Docker

- Get mongo image latest on docker hub
    ```Shell
        docker pull mongo:latest
    ```
- Run docker image, with port [27017], volume [mongodb-database], container name [mymongo]
    ```Shell
        docker run -d -p 27017:27017 --name mymongo mongo:latest
    ```
- Exec docker container
    ```Shell
        docker exec -it mymongo bash
    ```
- Show databases existed
    ```Shell
        docker exec -it mymongo bash
    ```
- Create database bookAPI and insert record to table database
    Copy query bookJson.js file and paste in command line
    ```Shell
        mongo
        use bookAPI
        [Copy & Paste query insert records]
    ```

# Docker Cheat Sheet

- Show no images loaded
    ```Shell
        docker images
    ```

- Show no containers running
    ```Shell
        docker ps -a
    ```
- Build the image
    ```Shell
        docker build -t simple-web:1.0.0 .
    ```

- Create a container and run it
    ```Shell
        docker run --name simple-web-container -p 8080:80 simple-web:1.0.0
    ```

- Stop and remove the containers
    ```Shell
        docker stop simple-web-container
        docker rm simple-web-container
    ```

- Remove the images
    ```Shell
        docker images
        docker rmi simple-web:1.0.0
    ```

- Alternate - remove all containers
    use the -f command if you want to stop and remove the containers. Be warned that this can be bad for your containers and should only be run in development.
    ```Shell
        docker rm $(docker ps -a -q)
    ```

- Alternate - remove all images
    Removes all images from your machine that are not currently being used for a container on your machine.
    ```Shell
        docker rmi $(docker images -q)
    ```

- Interacting with the container
    You can run commands on the running container using this command. In this example, we are running bash on the container in interactive mode from our command prompt.
    ```Shell
        docker exec -it <container ID or name> bash
    ```
- ##  Docker Compose
    - Starts up the orchestration process, builds the images (if needed), and launches the containers in order with the specified parameters. Use the -d for detached operation.
        ```Shell
            docker-compose up
        ```
    - Starts the orchestration process like above but rebuilds the containers if they already exist (rather than just using the existing containers).
        ```Shell
            docker-compose up --build
        ```
    - Stops the containers but does not remove them.
        ```Shell
            docker-compose stop
        ```
    - Stops and removes the containers.
        ```Shell
            docker-compose down
        ```

# Testing with Mocha
- Install package includes mocha, should, sinon
    ```Shell
        npm i -D mocha should sinon
    ```