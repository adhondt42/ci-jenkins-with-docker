FROM nginx:1.15
COPY certs/	/etc/ssl/	
COPY nginx_template.conf /etc/nginx/conf.d/
ENV PROJECT_DNS=${PROJECT_DNS}
ENV PROJECT_NAME=${PROJECT_NAME}
EXPOSE 80
EXPOSE 443
RUN bash -c "envsubst < /etc/nginx/conf.d/nginx_template.conf > /etc/nginx/conf.d/default.conf"
CMD ["nginx", "-g", "daemon off;"]