# docker_course_2021
Repo for the course <a href="https://devopswithdocker.com/" target="_blank">DevOps with Docker at University of Helsinki</a>


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
