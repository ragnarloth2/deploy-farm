FROM node:16

# Create app directory
WORKDIR /usr/src/app

# Bundle app source
COPY project_farm_api .

RUN pwd
RUN ls
RUN npm install

EXPOSE 3035
CMD [ "node", "./src/server.js" ]