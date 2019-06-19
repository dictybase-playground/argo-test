FROM node:10.4.0-alpine
ARG url
ENV GITHUB_REPO_URL ${url:-https://github.com/dictyBase/dicty-frontpage}
ARG organization
ENV GITHUB_REPO_ORGANIZATION ${organization:-dictyBase}
ARG name
ENV GITHUB_REPO_NAME ${name:-dicty-frontpage}
RUN apk update && apk upgrade && \
  apk add --no-cache bash git openssh jq
RUN mkdir -p /usr/src/app
WORKDIR /usr/src/app
ADD https://raw.githubusercontent.com/$GITHUB_REPO_ORGANIZATION/$GITHUB_REPO_NAME/develop/package.json ./
ADD https://raw.githubusercontent.com/$GITHUB_REPO_ORGANIZATION/$GITHUB_REPO_NAME/develop/package-lock.json ./
ADD $GITHUB_REPO_URL/tree/develop/src src
ADD $GITHUB_REPO_URL/tree/develop/public public
ENV NODE_PATH src
RUN npm install && npm run test