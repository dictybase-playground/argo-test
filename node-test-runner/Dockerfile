FROM node:10.4.0-alpine
RUN apk update && apk upgrade && \
  apk add --no-cache bash git openssh jq
RUN mkdir -p /usr/src/app
WORKDIR /usr/src/app
COPY package-lock.json ./
ADD package.json ./
ADD src src
ADD public public
ENV NODE_PATH src
RUN npm install && npm run test



# old code
# ENV GITHUB_WEBHOOK_CONTENTS $GITHUB_WEBHOOK_CONTENTS
# COPY print.js /
# ENTRYPOINT ["node", "./print.js"]