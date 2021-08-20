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
![screenshot](https://github.com/chpatola/docker_course_2021/blob/main/1.01/1.01.png?raw=true)

### Exercise 1.2
#### Task
We’ve left containers and a image that won’t be used anymore and are taking space, as docker ps -as and docker images will reveal.

Clean the docker daemon from all images and containers.

Submit the output for docker ps -a and docker images
#### Answers
![screenshot](https://github.com/chpatola/docker_course_2021/blob/main/1.02/1.02_images.png?raw=true)
![screenshot](https://github.com/chpatola/docker_course_2021/blob/main/1.02/1.02_containers.png?raw=true)

### Exercise 1.3
#### Task
Image devopsdockeruh/simple-web-service:ubuntu will start a container that outputs logs into a file. Go inside the container and use tail -f ./text.log to follow the logs. Every 10 seconds the clock will send you a “secret message”.

Submit the secret message and command(s) given as your answer.
#### Answers
![screenshot](https://github.com/chpatola/docker_course_2021/blob/main/1.03/1.03_attach_to_container.png)
![screenshot](https://github.com/chpatola/docker_course_2021/blob/main/1.03/1.03_pull_image.png)
![screenshot](https://github.com/chpatola/docker_course_2021/blob/main/1.03/1.03_start_container.png)

### Exercise 1.4
#### Task
Start a ubuntu image with the process sh -c 'echo "Input website:"; read website; echo "Searching.."; sleep 1; curl http://$website;'

You will notice that a few things required for proper execution are missing. Be sure to remind yourself which flags to use so that the read actually waits for input.

This time return the command you used to start process and the command(s) you used to fix the ensuing problems.
#### Answers
![screenshot](https://github.com/chpatola/docker_course_2021/blob/main/1.04/1.04_content.png)
![screenshot](https://github.com/chpatola/docker_course_2021/blob/main/1.04/1.04_command.png)

### Exercise 1.5
#### Task
In a previous exercise we used devopsdockeruh/simple-web-service:ubuntu.

Here is the same application but instead of ubuntu is using alpine: devopsdockeruh/simple-web-service:alpine.

Pull both images and compare the image sizes. Go inside the alpine container and make sure the secret message functionality is the same. Alpine version doesn’t have bash but it has sh.
#### Answers
![screenshot](https://github.com/chpatola/docker_course_2021/blob/main/1.05/1.05_images_sizes.png)
![screenshot](https://github.com/chpatola/docker_course_2021/blob/main/1.05/1.05_message.png)

### Exercise 1.6
#### Task
Run docker run -it devopsdockeruh/pull_exercise.

It will wait for your input. Navigate through docker hub to find the docs and Dockerfile that was used to create the image.

Read the Dockerfile and/or docs to learn what input will get the application to answer a “secret message”.

Submit the secret message and command(s) given to get it as your answer.
#### Answers
![screenshot](https://github.com/chpatola/docker_course_2021/blob/main/1.06/1.06.png)

### Exercise 1.7
#### Task
By default our devopsdockeruh/simple-web-service:alpine doesn’t have a CMD. It instead uses ENTRYPOINT to declare which application is run.

We’ll talk more about ENTRYPOINT in the next section, but you already know that the last argument in docker run can be used to give command.

As you might’ve noticed it doesn’t start the web service even though the name is “simple-web-service”. A command is needed to start the server!

Try docker run devopsdockeruh/simple-web-service:alpine hello. The application reads the argument but will inform that hello isn’t accepted.

In this exercise create a Dockerfile and use FROM and CMD to create a brand new image that automatically runs the server. Tag the new image as “web-server”

Return the Dockerfile and the command you used to run the container.
#### Answers
![screenshot](https://github.com/chpatola/docker_course_2021/blob/main/1.07/1.07_commands.png)
![screenshot](https://github.com/chpatola/docker_course_2021/blob/main/1.07/Dockerfile)