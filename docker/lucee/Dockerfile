FROM lucee/lucee52:5.2.4.37
ARG SERVER_CONTEXT="/opt/lucee/server/lucee-server/context"

RUN apt-get update && apt-get install -y uuid-runtime

# Copy over the Lucee Config Files
COPY config/lucee-server.xml /opt/lucee/server/lucee-server/context/lucee-server.xml
COPY config/lucee-web.xml.cfm /opt/lucee/web/lucee-web.xml.cfm
COPY config/server.xml /usr/local/tomcat/conf/server.xml
COPY config/web.xml /usr/local/tomcat/conf/web.xml
COPY config/context.xml /usr/local/tomcat/conf/context.xml
COPY config/setenv.sh /usr/local/tomcat/bin/setenv.sh

# Copy over the updated Lucee jars
COPY config/jars/* /opt/lucee/server/lucee-server/bundles/
COPY config/libs/* $SERVER_CONTEXT/lib/

RUN chmod a+x /usr/local/tomcat/bin/setenv.sh

# Expose Ports
EXPOSE 8888

COPY entrypoint.sh /entrypoint.sh
RUN chmod a+x /entrypoint.sh

ENTRYPOINT ["/entrypoint.sh"]

CMD ["catalina.sh", "run"]