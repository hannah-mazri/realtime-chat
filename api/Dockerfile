FROM node:14 AS development

# specify working directory inside container
WORKDIR /hnajwa/src/app

COPY package*.json ./

RUN npm install

# bundle app sources
COPY . .


RUN npm run build

EXPOSE 3000


##############
## PRODUCTION
##############

FROM node:14 as production

ARG NODE_ENV=production
ENV NODE_ENV=${NODE_ENV}}

WORKDIR /hnajwa/src/app

COPY --from=development /hnajwa/src/app/ .

EXPOSE 3000

# run app
CMD ["node", "dist/main"]