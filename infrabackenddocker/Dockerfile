FROM eclipse-temurin:17-jre
WORKDIR /usr/app
COPY target/products_api.jar .
EXPOSE 8080
ENTRYPOINT ["java","-jar","products_api.jar"]
