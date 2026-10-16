FROM fcrepo/fcrepo:7.0.0-tomcat10

COPY configFiles/fedora/web.xml /usr/local/tomcat/webapps/fcrepo/WEB-INF/
COPY configFiles/fedora/fcrepo.properties /usr/local/tomcat/fcrepo-home/config/fcrepo.properties

# Fedora 7 wires Apache Shiro (shiro-ee) via a @WebListener/ServletContainerInitializer,
# so it loads even when removed from web.xml. Authorization is disabled in this setup,
# so remove the Shiro jars entirely to stop EnvironmentLoaderListener from starting
# (it fails with NoClassDefFoundError: org/omnifaces/util/Lazy).
RUN rm -f /usr/local/tomcat/webapps/fcrepo/WEB-INF/lib/shiro-*.jar