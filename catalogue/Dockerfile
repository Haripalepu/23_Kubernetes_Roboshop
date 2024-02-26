FROM node:18.19.1-alpine3.19
EXPOSE 8080
RUN addgroup -S roboshop && adduser -S roboshop -G roboshop
WORKDIR /opt/server
#ENV MONGO=true #Passing it from configmap #Ref manifest file 7th line.
RUN chown roboshop:roboshop /opt/server
USER roboshop
COPY package.json /opt/server/
COPY server.js /opt/server/
RUN npm install
CMD ["node", "server.js"]


##CMD ["node", "server.js"]- to start the nodejs service. Systemctl commands will ot work in containers.

## Using alpine OS because it very light weight.