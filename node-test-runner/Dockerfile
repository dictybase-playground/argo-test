FROM node:10.4.0-alpine
ARG url
ENV GITHUB_REPO_URL ${url:-https://github.com/dictyBase/dicty-frontpage}
RUN apk update && apk upgrade && \
  apk add --no-cache bash git openssh jq
RUN mkdir -p /usr/src/app
WORKDIR /usr/src/app
COPY $GITHUB_REPO_URL/blob/develop/package.json ./
COPY $GITHUB_REPO_URL/blob/develop/package-lock.json ./
ADD $GITHUB_REPO_URL/tree/develop/src src
ADD $GITHUB_REPO_URL/tree/develop/public public
ENV NODE_PATH src
RUN npm install && npm run test