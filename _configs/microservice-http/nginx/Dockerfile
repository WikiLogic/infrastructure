FROM nginx

# Copy in the nginx configuration files
COPY ./_configs/microservice-http/nginx/mime.types /etc/nginx/mime.types
COPY ./_configs/microservice-http/nginx/nginx.conf /etc/nginx/nginx.conf

# Copy the static files into the default nginx directory
COPY ./react-app/dist/static /var/www/app/static
COPY ./react-app/dist/index.html /var/www/app/index.html

# Define default command.
CMD ["nginx"]

# Expose port
EXPOSE 80