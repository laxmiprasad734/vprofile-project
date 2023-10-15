FROM openjdk:11 AS BUIlD_IMAGE
RUN apt update && apt install maven -y
RUN git clone https://github.com/laxmiprasad734/vprofile-project.git
RUN cd vprofile-project && git checkout docker && mvn install

FROM tomcat:9-jre11
LABEL "Project"="Vprofile"
LABEL "Author"="laxmiprasad734"
RUN rm -rf /usr/local/tomcat/webapps/*
COPY --from=BUIlD_IMAGE vprofile-project/target/vprofile-v2.war /usr/local/tomcat/webapps/ROOT.war

EXPOSE 8080
CMD ["catalina.sh", "run"]
