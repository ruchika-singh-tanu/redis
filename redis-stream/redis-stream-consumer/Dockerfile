# Use JRE11 slim
FROM openjdk:18-alpine
# Add the app jar
ADD target/*.jar redis-stream.jar

ENTRYPOINT java -jar redis-stream.jar