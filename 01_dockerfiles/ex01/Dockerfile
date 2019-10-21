FROM debian

ENV TS3SERVER_LICENSE accept

EXPOSE 9987/udp 30033 10011

RUN apt-get update && \
	apt-get install curl -y && \
	apt-get install bzip2 -y && \
	curl -O http://dl.4players.de/ts/releases/3.8.0/teamspeak3-server_linux_amd64-3.8.0.tar.bz2 && \
	bzip2 -d teamspeak3-server_linux_amd64-3.8.0.tar.bz2 && \
	tar -xf teamspeak3-server_linux_amd64-3.8.0.tar

ENTRYPOINT sh ./teamspeak3-server_linux_amd64/ts3server_minimal_runscript.sh
