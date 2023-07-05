FROM hzkjhub/java17:17.0.4
RUN yum install git -y
RUN git clone https://github.com/spring-petclinic/spring-framework-petclinic.git
RUN cd spring-framework-petclinic
WORKDIR spring-framework-petclinic
EXPOSE 8080
CMD [ "./mvnw", "jetty:run-war"]
