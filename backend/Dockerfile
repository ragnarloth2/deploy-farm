FROM node:16

# Create app directory
WORKDIR /usr/src/app

# Bundle app source
COPY project_farm_api .

RUN pwd
RUN cd project_farm_api && npm install

EXPOSE 3035
CMD [ "node", "/project_farm_api/src/server.js" ]