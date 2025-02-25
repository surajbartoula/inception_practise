FROM debian:bullseye

# Install necessary packages
RUN apt-get update && apt-get install -y nginx openssl \
    && rm -rf /var/lib/apt/lists/*

# Remove default config and copy our custom one
RUN rm /etc/nginx/sites-enabled/default
COPY nginx.conf /etc/nginx/nginx.conf

# Create SSL directory
RUN mkdir -p /etc/nginx/ssl

# Copy SSL certificates (or generate your own)
COPY certs/server.crt /etc/nginx/ssl/server.crt
COPY certs/server.key /etc/nginx/ssl/server.key

# Expose HTTPS port
EXPOSE 443

# Start NGINX
CMD ["nginx", "-g", "daemon off;"]
