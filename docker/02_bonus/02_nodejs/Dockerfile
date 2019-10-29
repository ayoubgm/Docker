FROM	node

WORKDIR	/var/www/app

RUN apt-get update && apt-get install -y apt-transport-https
RUN curl -sS https://dl.yarnpkg.com/debian/pubkey.gpg | apt-key add -
RUN echo "deb https://dl.yarnpkg.com/debian/ stable main" | tee /etc/apt/sources.list.d/yarn.list
RUN apt-get update && apt-get install yarn -y

COPY app /var/www/app

RUN yarn install

CMD ["node", "app.js"]

#docker run -it --rm -p 3000:3000 image_nodejs
