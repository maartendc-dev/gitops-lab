# Use official nginx image
FROM docker.io/library/nginx:latest

# Install envsubst (part of gettext) to replace $POD_NAME in HTML
RUN apt-get update && apt-get install -y gettext-base && rm -rf /var/lib/apt/lists/*

# Copy your HTML5 UP Lens site
COPY html5up-lens/ /usr/share/nginx/html

# Replace $POD_NAME in index.html at container start and start nginx
CMD sh -c "envsubst '\$POD_NAME' < /usr/share/nginx/html/index.html > /usr/share/nginx/html/index2.html && mv /usr/share/nginx/html/index2.html /usr/share/nginx/html/index.html && nginx -g 'daemon off;'"
