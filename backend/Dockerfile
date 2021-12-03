FROM node

COPY project_farm_api .

RUN yarn

EXPOSE 3035
CMD [ "node ./src/server.js" ]