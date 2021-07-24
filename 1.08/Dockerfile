FROM ubuntu:18.04
WORKDIR /1.8
COPY curling.sh .
RUN chmod +x curling.sh
RUN apt-get update && apt-get install -y curl 
CMD ./curling.sh