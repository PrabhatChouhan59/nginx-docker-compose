FROM nginx:alpine


# Remove default nginx website
RUN rm -rf /usr/share/nginx/html/*

COPY index.html /usr/share/nginx/html/
COPY static/ /usr/share/nginx/html/static/


# Copy nginx configuration
COPY nginx.conf /etc/nginx/nginx.conf

EXPOSE 80

CMD ["nginx", "-g", "daemon off;"]