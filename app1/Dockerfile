# Usa a iamgem oficial dp PHP com Apache
FROM php:8.2-apache

# Porta usada pelo Render 
ENV PORT=8080

# Ativa o mod_rewrite para URLs amigaveis 
RUN a2emod rewrite

# Copia o codigo da aplicvação 
COPY ./var/www/html/

# Corrige permissoes 
RUN chown -R ww-data:www-data /var/www/html && chmod -R 755 /var/www/htm

# Corrige configurção da porta 
RUN sed -i "s/Listen 80/Listen ${PORT}/" /etc/apache2/apache2/ports.conf && \
sed -i "s/VirtualHost \*:80>/VirtualHost \*:${PORT}>/" /etec/apache2/sites-available/000-defaul.conf

#Permite acesso ao diretorio
RUN echo '<Directory /var/www/html>' >> /etc/apache2/apache2.conf && \
echo ' Options Indexes FollowSymLinks' >> /etc/apache2/apache2.conf && \
echo ' AllowOveride All' >> /etc/apache2/apache2.conf && \
echo ' Require all grated' >> /etc/apache2/apache2.conf && \
echo '</Directory>' >> /etc/apache2/apache2.conf

#Expõe a porta corretamente 
EXPOSE ${PORT}
