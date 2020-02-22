FROM	alpine

RUN		apk update &&\
		apk upgrade &&\
		apk add apache2-ssl apache2-utils ca-certificates htop

ENTRYPOINT	["ab"]

#docker run --rm image_ab -v 2 https://www.docker.com/
