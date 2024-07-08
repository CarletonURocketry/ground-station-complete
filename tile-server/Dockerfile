FROM nginx:latest

# Set the working directory in the container
WORKDIR /usr/src/app

# Copy the nginx configuration file
COPY nginx.conf /etc/nginx/nginx.conf

# Copy the mapping tiles
# COPY --from=unzipper /mapping_tiles /usr/src/app/mapping_tiles

# Create mount point for the mapping tiles
RUN mkdir -p /usr/src/app/mapping_tiles

# Create a directory for the cache
RUN mkdir -p /var/cache/nginx && chown -R nginx:nginx /var/cache/nginx

# Expose port 80
EXPOSE 80 

WORKDIR /usr/src/app/mapping_tiles

# Run the app when the container launches
CMD ["nginx", "-g", "daemon off;"]