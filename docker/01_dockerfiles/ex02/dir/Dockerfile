FROM ruby

RUN apt-get update -y &&\
	apt-get install -y nodejs &&\
	gem update &&\
	gem install rails

ONBUILD ADD			app /opt/app
ONBUILD WORKDIR 	/opt/app/
ONBUILD RUN			bundle install
ONBUILD RUN			bin/rake db:migrate
ONBUILD RUN			bin/rake db:seed
