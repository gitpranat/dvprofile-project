FROM openjdk:11 AS BUILD_IMAGE
RUN apt update && apt install maven -y
RUN git clone https://github.com/gitpranat/dvprofile-project.git
RUN cd dvprofile-project && git checkout docker && mvn install 

FROM tomcat:9-jre11
LABEL "Project"="Vprofile"
LABEL "Auther"="Pranat"
RUN rm -rf /usr/local/tomcat/webaps/*
COPY --from=BUILD_IMAGE dvprofile-project/target/vprofile-v2.war /usr/local/tomcat/webaps/ROOT.war

EXPOSE 8080
CMD ["catalina.sh", "run"]