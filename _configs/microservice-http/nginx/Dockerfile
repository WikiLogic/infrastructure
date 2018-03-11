FROM nginx

# Copy the static files into the default nginx directory
COPY ../../react-app/dist /usr/share/nginx/html





# Install Nginx
RUN apt-get update
RUN apt-get install -y nginx
RUN rm -rf /var/lib/apt/lists/*
RUN chown -R www-data:www-data /var/lib/nginx

# sharing the static files! 
VOLUME ["/var/www/app", "/etc/letsencrypt/live", "/etc/nginx"] 

# Define default command.
CMD ["nginx"]

# Expose ports.
EXPOSE 80
EXPOSE 443