#Dockerfile
FROM openjdk:8

WORKDIR /app

COPY . .

RUN ./mvnw package

CMD ["java", "-jar","./target/docker-example-1.1.3.jar"]

#Commands
docker build -t my-java-app .
docker run -p 8000:8080 my-java-app

