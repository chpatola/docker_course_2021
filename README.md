# Docker course 2021
Repo for the course <a href="https://devopswithdocker.com/" target="_blank">DevOps with Docker at University of Helsinki</a>

Note: As I do not have sudo rights to my university computer, I did the exercises on an azure virtual machine.


### Exercise 1.1
#### Task
Since we already did “Hello, World!” in the material let’s do something else.

Start 3 containers from image that does not automatically exit, such as nginx, detached.

Stop 2 of the containers leaving 1 up.

Submit the output for docker ps -a which shows 2 stopped containers and one running.
#### Answer
![screenshot](https://github.com/chpatola/docker_course_2021/blob/main/part1/1.01/1.01.png?raw=true)

### Exercise 1.2
#### Task
We’ve left containers and a image that won’t be used anymore and are taking space, as docker ps -as and docker images will reveal.

Clean the docker daemon from all images and containers.

Submit the output for docker ps -a and docker images
#### Answers
![screenshot](https://github.com/chpatola/docker_course_2021/blob/main/part1/1.02/1.02_images.png?raw=true)
![screenshot](https://github.com/chpatola/docker_course_2021/blob/main/part1/1.02/1.02_containers.png?raw=true)

### Exercise 1.3
#### Task
Image devopsdockeruh/simple-web-service:ubuntu will start a container that outputs logs into a file. Go inside the container and use tail -f ./text.log to follow the logs. Every 10 seconds the clock will send you a “secret message”.

Submit the secret message and command(s) given as your answer.
#### Answers
![screenshot](https://github.com/chpatola/docker_course_2021/blob/main/part1/1.03/1.03_attach_to_container.png)
![screenshot](https://github.com/chpatola/docker_course_2021/blob/main/part1/1.03/1.03_pull_image.png)
![screenshot](https://github.com/chpatola/docker_course_2021/blob/main/part1/1.03/1.03_start_container.png)

### Exercise 1.4
#### Task
Start a ubuntu image with the process sh -c 'echo "Input website:"; read website; echo "Searching.."; sleep 1; curl http://$website;'

You will notice that a few things required for proper execution are missing. Be sure to remind yourself which flags to use so that the read actually waits for input.

This time return the command you used to start process and the command(s) you used to fix the ensuing problems.
#### Answers
Commands:![screenshot](https://github.com/chpatola/docker_course_2021/blob/main/part1/1.04/1.04_command.png)
Takes input:![screenshot](https://github.com/chpatola/docker_course_2021/blob/main/part1/1.04/1.04_content.png)

### Exercise 1.5
#### Task
In a previous exercise we used devopsdockeruh/simple-web-service:ubuntu.

Here is the same application but instead of ubuntu is using alpine: devopsdockeruh/simple-web-service:alpine.

Pull both images and compare the image sizes. Go inside the alpine container and make sure the secret message functionality is the same. Alpine version doesn’t have bash but it has sh.
#### Answers
![screenshot](https://github.com/chpatola/docker_course_2021/blob/main/part1/1.05/1.05_images_sizes.png)
![screenshot](https://github.com/chpatola/docker_course_2021/blob/main/part1/1.05/1.05_message.png)

### Exercise 1.6
#### Task
Run docker run -it devopsdockeruh/pull_exercise.

It will wait for your input. Navigate through docker hub to find the docs and Dockerfile that was used to create the image.

Read the Dockerfile and/or docs to learn what input will get the application to answer a “secret message”.

Submit the secret message and command(s) given to get it as your answer.
#### Answers
![screenshot](https://github.com/chpatola/docker_course_2021/blob/main/part1/1.06/1.06.png)

### Exercise 1.7
#### Task
By default our devopsdockeruh/simple-web-service:alpine doesn’t have a CMD. It instead uses ENTRYPOINT to declare which application is run.

We’ll talk more about ENTRYPOINT in the next section, but you already know that the last argument in docker run can be used to give command.

As you might’ve noticed it doesn’t start the web service even though the name is “simple-web-service”. A command is needed to start the server!

Try docker run devopsdockeruh/simple-web-service:alpine hello. The application reads the argument but will inform that hello isn’t accepted.

In this exercise create a Dockerfile and use FROM and CMD to create a brand new image that automatically runs the server. Tag the new image as “web-server”

Return the Dockerfile and the command you used to run the container.
#### Answers
![screenshot](https://github.com/chpatola/docker_course_2021/blob/main/part1/1.07/1.07_commands.png)
![dockerfile](https://github.com/chpatola/docker_course_2021/blob/main/part1/1.07/Dockerfile)

### Exercise 1.8
#### Task
Create a Dockerfile for a new image that starts from ubuntu:18.04.

Make a script file on you local machine with such content as echo "Input website:"; read website; echo "Searching.."; sleep 1; curl http://$website;. Transfer this file to an image and run it inside the container using CMD. Build the image with tag “curler”.

Run the new curler image with the correct flags and input helsinki.fi into it. Output should match the 1.4 one.

Return both Dockerfile and the command you used to run the container.
#### Answers
![screenshot](https://github.com/chpatola/docker_course_2021/blob/main/part1/1.08/1.08_command.png)
![dockerfile](https://github.com/chpatola/docker_course_2021/blob/main/part1/1.08/Dockerfile)

### Exercise 1.9
#### Task
Image devopsdockeruh/simple-web-service creates a timestamp every two seconds to /usr/src/app/text.log when it’s not given a command. Start the container with bind mount so that the logs are created into your filesystem.

Submit the command you used to complete the exercise.
#### Answers
![screenshot](https://github.com/chpatola/docker_course_2021/blob/main/part1/1.09/1.09_set_up_local.png)
![screenshot](https://github.com/chpatola/docker_course_2021/blob/main/part1/1.09/1.09_container_command.png)

### Exercise 1.10
#### Task
Image devopsdockeruh/simple-web-service will start a web service in port 8080 when given the command “server”. From 1.7 you should have an image ready for this. Use -p flag to access the contents with your browser. The output to your browser should be something like: { message: "You connected to the following path: ...

Submit your used commands for this exercise.
#### Answers
![screenshot](https://github.com/chpatola/docker_course_2021/blob/main/part1/1.10/1.10_commands_start_container.png)
![screenshot](https://github.com/chpatola/docker_course_2021/blob/main/part1/1.10/1.10_connected_to_localhost.png)

### Exercise 1.11
#### Task
Lets create a Dockerfile for a Java Spring project: github page

The setup should be straightforward with the README instructions. Tips to get you started:

Use openjdk image FROM openjdk:_tag_ to get java instead of installing it manually. Pick the tag by using the README and dockerhub page.

You’ve completed the exercise when you see a ‘Success’ message in your browser.
#### Answers
![screenshot](https://github.com/chpatola/docker_course_2021/blob/main/part1/1.11/1.11_run_command.png)
![screenshot](https://github.com/chpatola/docker_course_2021/blob/main/part1/1.11/1.11_html_output.png)
![dockerfile](https://github.com/chpatola/docker_course_2021/blob/main/part1/1.11/Dockerfile)

### Exercise 1.12
#### Task
Clone, fork or download the project from https://github.com/docker-hy/material-applications/tree/main/part1/example-frontend.

Create a Dockerfile for the project (example-frontend) and give a command so that the project runs in a docker container with port 5000 exposed and published so when you start the container and navigate to http://localhost:5000 you will see message if you’re successful.

Submit the Dockerfile.
#### Answers
![screenshot](https://github.com/chpatola/docker_course_2021/blob/main/part1/1.12/1.12_commands_run.png)
![dockerfile](https://github.com/chpatola/docker_course_2021/blob/main/part1/1.12/Dockerfile)

### Exercise 1.13
#### Task
Clone, fork or download a project from https://github.com/docker-hy/material-applications/tree/main/part1/example-backend.

Create a Dockerfile for the project (example-backend) and give a command so that the project runs in a docker container with port 8080 published.

When you start the container and navigate to http://localhost:8080/ping you should get a “pong” as response.

Submit the Dockerfile and the command used.
#### Answers
![screenshot](https://github.com/chpatola/docker_course_2021/blob/main/part1/1.13/1.13_commands.png)
![dockerfile](https://github.com/chpatola/docker_course_2021/blob/main/part1/1.13/Dockerfile)

### Exercise 1.14
#### Task
Start both frontend-example and backend-example with correct ports exposed and add ENV to Dockerfile with necessary information from both READMEs (front,back).

Ignore the backend configurations until frontend sends requests to _backend_url_/ping when you press the button.

You know that the configuration is ready when the button for 1.14 of frontend-example responds and turns green.

Submit the edited Dockerfiles and commands used to run.
#### Answers
![Backend data](https://github.com/chpatola/docker_course_2021/tree/main/part1/1.14/Backend)
![Frontend data](https://github.com/chpatola/docker_course_2021/tree/main/part1/1.14/Frontend)

### Exercise 1.15
#### Task
Create Dockerfile for an application or any other dockerised project in any of your own repositories and publish it to Docker Hub. This can be any project except clones / forks of backend-example or frontend-example.

For this exercise to be complete you have to provide the link to the project in docker hub, make sure you at least have a basic description and instructions for how to run the application in a README that’s available through your submission.
#### Answers
Link to docker repo:https://hub.docker.com/repository/docker/chpatola/yle_web

Link to github repo incl Readme: https://github.com/chpatola/yle_web

### Exercise 1.16
#### Task
Pushing to heroku happens in a similar way. A project has already been prepared at devopsdockeruh/heroku-example so lets pull that first. Note that the image of the project is quite large.

Go to https://www.heroku.com/ and create a new app there and install heroku CLI. You can find additional instructions from Deploy tab under Container Registry. Tag the pulled image as registry.heroku.com/_app_/_process-type_, process-type can be web for this exercise. The app should be your project name in heroku.

Then push the image to heroku with docker push registry.heroku.com/_app_/web and release it using the heroku CLI: heroku container:release web (you might need to login first: heroku container:login)

For this exercise return the url in which the released application is.
#### Answers
Link to app:https://hkiunidocker.herokuapp.com/