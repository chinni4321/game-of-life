FROM ubuntu
RUN apt-get update && apt-get install wget -y
RUN mkdir /usr/app
WORKDIR /usr/app
#RUN cd workspace
COPY game-of-life/gameoflife-build/target/gameoflife-build-1.0-SNAPSHOT.jar /usr/app
