# Imagen de apache
FROM httpd:latest

# Copiamos nuestro VirtualHost personalizado
COPY my-proxy.conf /usr/local/apache2/conf/extra/my-proxy.conf

# Incluir el archivo en la configuración principal
RUN echo "Include conf/extra/my-proxy.conf" >> /usr/local/apache2/conf/httpd.conf
