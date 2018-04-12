FROM node

WORKDIR /var/www/api/

# Install the API in /var/www/api/
WORKDIR /var/www/api/
COPY ./api/package.json ./package.json
COPY ./api/package-lock.json ./package-lock.json
RUN npm install
RUN npm install nodemon -g

# Copy the api files in
COPY ./api/api.js ./api.js
COPY ./api/src ./src

# Define default command. Using pm2 to run the API in production http://pm2.keymetrics.io/
# CMD ["pm2-docker", "api.js"]
CMD ["nodemon", "--legacy-watch", "api.js"]

# Expose ports.
EXPOSE 3030