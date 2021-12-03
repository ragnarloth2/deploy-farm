FROM node:16

# Create app directory
WORKDIR /usr/src/app

# Bundle app source
COPY project_farm_api /

#RUN cd /project_farm_api && npm install
# If you are building your code for production
# RUN npm ci --only=production

EXPOSE 3035
CMD [ "node", "/project_farm_api/src/server.js" ]