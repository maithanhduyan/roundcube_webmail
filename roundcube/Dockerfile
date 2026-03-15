FROM roundcube/roundcubemail:latest

# Remove mpm_event module entirely to prevent "More than one MPM loaded" error
RUN rm -f /etc/apache2/mods-enabled/mpm_event.load /etc/apache2/mods-enabled/mpm_event.conf \
 && rm -f /etc/apache2/mods-enabled/mpm_worker.load /etc/apache2/mods-enabled/mpm_worker.conf

# Railway assigns a dynamic PORT via $PORT env var
ENV APACHE_PORT=${PORT:-80}
COPY roundcube/docker-entrypoint-wrapper.sh /docker-entrypoint-wrapper.sh
RUN chmod +x /docker-entrypoint-wrapper.sh

ENTRYPOINT ["/docker-entrypoint-wrapper.sh"]
CMD ["apache2-foreground"]
