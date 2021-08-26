FROM node:14 AS development

WORKDIR /hnajwa/src/app

COPY package*.json ./

RUN npm install

COPY . .

RUN npm run build

EXPOSE 3000

################
## PRODUCTION ##
################
FROM node:14 AS production

ARG NODE_ENV=production
ENV NODE_ENV=${NODE_ENV}

WORKDIR /hnajwa/src/app

COPY --from=development /hnajwa/src/app/ .

EXPOSE 3000

CMD ["node", "dist/main"]