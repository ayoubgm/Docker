FROM		debian

RUN		apt-get update
		apt-get upgrade -y
		apt-get install -y netcat --no-install-recommends

ENTRYPOINT	["netcat"]
