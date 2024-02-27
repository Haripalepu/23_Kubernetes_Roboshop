
#Build

FROM maven AS build

WORKDIR /opt/shipping

COPY pom.xml /opt/shipping/
RUN mvn dependency:resolve
COPY src /opt/shipping/src/
RUN mvn package

#
# Run
#
FROM openjdk:8-jre-alpine3.9

EXPOSE 8080

WORKDIR /opt/shipping

COPY --from=build /opt/shipping/target/shipping-1.0.jar shipping.jar

CMD [ "java", "-Xmn256m", "-Xmx768m", "-jar", "shipping.jar" ]




## Multi stage build
## To build the image we need JDK
## To run the container we need JRE
## JDK contains JRE
## JDK is having so we can build image using JDK and then while executing it we need only JRE. JDK is heavy size so while running the container JRE is enough why to increase image size by installing JDK.