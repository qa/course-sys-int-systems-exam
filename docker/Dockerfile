FROM fedora
WORKDIR /root
RUN dnf install -y java-1.8.0-openjdk-devel unzip git maven wget
RUN http://download.jboss.org/wildfly/9.0.1.Final/wildfly-9.0.1.Final.zip -o wildfly.zip
RUN unzip zips/wildfly.zip
ADD launch.sh launch.sh
ADD config.cli config.cli
ADD supplier.war supplier.war
EXPOSE 9092 8080
RUN wildfly-9.0.1.Final/bin/jboss-cli.sh --file=config.cli
RUN rm -rf wildfly-9.0.1.Final/standalone/configuration/standalone_xml_history wildfly-9.0.1.Final/standalone/tmp wildfly-9.0.1.Final/standalone/log
ENTRYPOINT /bin/sh /root/launch.sh
