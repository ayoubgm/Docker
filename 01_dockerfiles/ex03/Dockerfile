FROM		ubuntu

RUN			apt-get update &&\
			apt-get upgrade -y &&\
			apt-get install curl openssh-server postfix tzdata -y

RUN			curl -O https://packages.gitlab.com/install/repositories/gitlab/gitlab-ce/script.deb.sh && \
			chmod 777 script.deb.sh && ./script.deb.sh && apt-get install gitlab-ce -y

EXPOSE		80 443 1337

RUN			mkdir /etc/gitlab/ssl
RUN			openssl req -x509 -nodes -days 365 -newkey rsa:2048 -keyout /etc/gitlab/ssl/gitlab_key.key -out\
			/etc/gitlab/ssl/gitlab_cert.crt -subj "/C=MR/ST=Khouribga/L=Beni mellal-Khenifra/O=Khouribga Combany/CN=i.guismi@gmail.com"
RUN			rm /etc/gitlab/gitlab.rb
RUN			echo "external_url 'https://10.12.3.9'" >> /etc/gitlab/gitlab.rb
RUN			echo "gitlab_rails['gitlab_shell_ssh_port'] = 1337" >> /etc/gitlab/gitlab.rb
RUN			echo "nginx['redirect_http_to_https'] = true" >> /etc/gitlab/gitlab.rb
RUN			echo "nginx['ssl_certificate'] = '/etc/gitlab/ssl/gitlab_cert.crt'" >> /etc/gitlab/gitlab.rb
RUN			echo "nginx['ssl_certificate_key'] = '/etc/gitlab/ssl/gitlab_key.key'" >> /etc/gitlab/gitlab.rb
RUN			sed -i '/Port 22/s/^#//g' /etc/ssh/ssh_config
RUN			sed -i 's/Port 22/Port 1337/g' /etc/ssh/ssh_config
RUN			sed -i '/Port 22/s/^#//g' /etc/ssh/sshd_config
RUN			sed -i 's/Port 22/Port 1337/g' /etc/ssh/sshd_config
RUN			sed -i '/Port 22/s/^#//g' /etc/ssh/ssh_config
RUN			/etc/init.d/ssh restart

ENTRYPOINT	/opt/gitlab/embedded/bin/runsvdir-start& gitlab-ctl reconfigure
