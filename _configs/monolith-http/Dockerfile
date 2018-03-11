# This Dockerfile packages Wikilogic up into a single image to run without ssl
# docker build -t wl-mono-http .
# docker run -e ARANGO_NO_AUTH=1 -it -p 80:80 wl-mono-http
FROM ubuntu:16.04
MAINTAINER Iain J McCallum
ENV NPM_CONFIG_LOGLEVEL warn

# pulling the arango stuff from that 
ENV ARCHITECTURE amd64
ENV DEB_PACKAGE_VERSION 1
ENV ARANGO_VERSION 3.3.4
ENV ARANGO_URL https://download.arangodb.com/arangodb33/Debian_9.0
ENV ARANGO_PACKAGE arangodb3-${ARANGO_VERSION}-${DEB_PACKAGE_VERSION}_${ARCHITECTURE}.deb
ENV ARANGO_PACKAGE_URL ${ARANGO_URL}/${ARCHITECTURE}/${ARANGO_PACKAGE}
ENV ARANGO_SIGNATURE_URL ${ARANGO_PACKAGE_URL}.asc

# resync package indexes
RUN apt-get update -qq
RUN apt-get install -y --no-install-recommends gpg dirmngr
# install nginx
RUN apt-get install -y nginx
# install node
# RUN cd Downloads
RUN curl -sL https://deb.nodesource.com/setup_9.x
# RUN chmod +x setup_9.x
RUN apt-get install -y nodejs
# install npm
RUN apt-get install -y build-essential libssl-dev
RUN apt-get install -y npm
# installs a symlink needed by many modules to build correctly
RUN apt-get install -y nodejs-legacy


# nginx thing? purge lists?
RUN rm -rf /var/lib/apt/lists/*
# ?
RUN chown -R www-data:www-data /var/lib/nginx

# Copy in the nginx configuration files
COPY ./mime.types /etc/nginx/mime.types
COPY ./nginx.conf /etc/nginx/nginx.conf


# Install the API into /var/www/api/
WORKDIR /var/www/api/
COPY ../../api/package.json ./package.json
COPY ../../api/package-lock.json ./package-lock.json
RUN npm install
RUN npm install nodemon -g

# Copy the api files in
COPY ../../api/api-server.js ./api-server.js
COPY ../../api/src ./src

# Copy the FED files into /var/www/static/
WORKDIR /var/www/
COPY ../../react-app/dist/static static/
COPY ../../react-app/dist/index.html ./

# Define default command.
# write up a boot up script file?
# sudo systemctl start nginx 
WORKDIR /var/www/api
CMD ["arangodb", "&&", "npm", "start", "&&", "nginx"]

# Expose ports.
EXPOSE 80