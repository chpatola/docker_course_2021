# Docker course 2021
Repo for the course <a href="https://devopswithdocker.com/" target="_blank">DevOps with Docker at University of Helsinki</a>

Note 1: More files and/or screenshots than listed in the Readme may be available in the corresponding folders

Note 2: As I do not have sudo rights to my university computer, I did the exercises on an azure virtual machine.

## PART 1

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

## PART 2

### Exercise 2.1
#### Task
Create a docker-compose.yml file that starts devopsdockeruh/simple-web-service and saves the logs into your filesystem.

Submit the docker-compose.yml, make sure that it works simply by running docker-compose up if the log file exists.
#### Answers
![docker-compose](https://github.com/chpatola/docker_course_2021/blob/main/part2/2.01/docker-compose.yml)

### Exercise 2.2
#### Task
The familiar image devopsdockeruh/simple-web-service can be used to start a web service.

Create a docker-compose.yml and use it to start the service so that you can use it with your browser.

Submit the docker-compose.yml, make sure that it works simply by running docker-compose up
#### Answers
![docker-compose](https://github.com/chpatola/docker_course_2021/blob/main/part2/2.02/docker-compose.yml)

### Exercise 2.3
#### Task
In the previous part we created Dockerfiles for both frontend and backend. Next, simplify the usage into one docker-compose.yml.

Configure the backend and frontend from part 1 to work in docker-compose.

Submit the docker-compose.yml
#### Answers
![docker-compose](https://github.com/chpatola/docker_course_2021/blob/main/part2/2.03/docker-compose.yaml)

### Exercise 2.4
#### Task
Add redis to example backend.

Redis is used to speed up some operations. Backend uses a slow api to get information. You can test the slow api by requesting /ping?redis=true with curl. The frontend program has a button to test this.

Configure a redis container to cache information for the backend. Use the documentation if needed when configuring: https://hub.docker.com/_/redis/

Submit the docker-compose.yml
#### Answers
![docker-compose](https://github.com/chpatola/docker_course_2021/blob/main/part2/2.04/docker-compose.yaml)

### Exercise 2.5
#### Task
A project over at https://github.com/docker-hy/material-applications/tree/main/scaling-exercise has a hardly working application. Go ahead and clone it for yourself. The project already includes docker-compose.yml so you can start it by running docker-compose up.

Application should be accessible through http://localhost:3000. However it doesn’t work well enough and I’ve added a load balancer for scaling. Your task is to scale the compute containers so that the button in the application turns green.

Please return the used commands for this exercise.
#### Answers
![command](https://github.com/chpatola/docker_course_2021/blob/main/part2/2.05/2.5_command.png)
![docker-compose](https://github.com/chpatola/docker_course_2021/blob/main/part2/2.05/docker-compose.yaml)

### Exercise 2.6
#### Task
Add database to example backend.

Lets use a postgres database to save messages. We won’t need to configure a volume since the official postgres image sets a default volume for us. Lets use the postgres image documentation to our advantage when configuring: https://hub.docker.com/_/postgres/. Especially part Environment Variables is of interest.

Submit the docker-compose.yml
#### Answers
![Dockerfile](https://github.com/chpatola/docker_course_2021/blob/main/part2/2.06/Dockerfile)
![docker-compose](https://github.com/chpatola/docker_course_2021/blob/main/part2/2.06/docker-compose.yaml)

### Exercise 2.7
#### Task
Configure a machine learning project.

Look into machine learning project created with Python and React and split into three parts: frontend, backend and training

Note that the training requires 2 volumes and backend should share volume /src/model with training.

The frontend will display on http://localhost:3000 and the application will tell if the subject of an image looks more like a cucumber or a moped.

Submit the docker-compose.yml
#### Answers
![docker-compose](https://github.com/chpatola/docker_course_2021/blob/main/part2/2.07/docker-compose.yaml)

### Exercise 2.8
#### Task
Add nginx to example frontend + backend.
At the end you should see that the frontend is accessible simply by going to http://localhost and the button works. Other buttons may have stopped working, do not worry about them.

...

Submit the docker-compose.yml
#### Answers
![docker-compose](https://github.com/chpatola/docker_course_2021/blob/main/part2/2.08/docker-compose.yaml)

### Exercise 2.9
#### Task
Postgres image uses a volume by default. Manually define volumes for the database in convenient location such as in ./database . Use the image documentations (postgres) to help you with the task. You may do the same for redis as well.

After you have configured the volume:

Save a few messages through the frontend
Run docker-compose down
Run docker-compose up and see that the messages are available after refreshing browser
Run docker-compose down and delete the volume folder manually
Run docker-compose up and the data should be gone
Maybe it would be simpler to back them up now that you know where they are.

Submit the docker-compose.yml
#### Answers
![docker-compose](https://github.com/chpatola/docker_course_2021/blob/main/part2/2.09/docker-compose.yaml)

### Exercise 2.10
#### Task
Some buttons may have stopped working in the frontend + backend project. Make sure that every button for exercises works.

This may need a peek into the browsers developer consoles again like back part 1. The buttons of nginx exercise and the first button behave differently but you want them to match.

If you had to do any changes explain what you had to change.

Submit the docker-compose yml and both dockerfiles.
#### Answers
Explanation: 
In order to get all buttons of the app to function, I did this:

0. Started the app version from exercise 2.8 and looked at the information in the browser's developer tool's network tab.
   I saw that the 2.8 button - that worked - sent requests to another backend url than the buttons that did not work
1. Change REACT_APP_BACKEND_URL in frontend docker file to http://localhost/api 
2. Build the frontend again
3. Create a new docker-compose.yaml based on the ones used for exercises 2.8 and 2.9 + substitute front2 image for front3


![docker-compose](https://github.com/chpatola/docker_course_2021/blob/main/part2/2.10/docker-compose.yaml)
![Backend-dockerfile](https://github.com/chpatola/docker_course_2021/blob/main/part2/2.10/backend/Dockerfile)
![Frontend-dockerfile](https://github.com/chpatola/docker_course_2021/blob/main/part2/2.10/frontend/Dockerfile)

### Exercise 2.11
#### Task
Select a project that you already have and start utilizing containers in the development environment.

Explain what you have done. It can be anything, ranging from having supporting docker-compose.yml to have services containerized to developing inside a container.
#### Answers
As I cannot use Docker on my Uni computer, I find it very tricky to utilize it for development in my own, personal projects. 

At my work computer, I do not have sudo rights either but due to that, I have a virtualization environment where I do most of the development. There has been a little talk about the possibility to utilize Docker for development projects that more than one person is involved in or for larger projects. Currently, our team mostly work in R and do not publish apps or API:s. However, it might be something we start doing more in the future. When I am back from my study leave, I will look into if Docker could be utilized in any of our current projects. 