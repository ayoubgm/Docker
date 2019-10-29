FROM		alpine

RUN		apk update\
		apk upgrade\
		apk apache2-ssl\
		apk apache2-utils\
		ca-certificates\
		htop

ENTRYPOINT	["ab"]
#docker run --rm image_ab -v 2 https://www.docker.com/
