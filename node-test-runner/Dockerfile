FROM node:10.4.0-alpine
ENV GITHUB_REPO_URL $GITHUB_REPO_URL
ENV GITHUB_REPO_BRANCH $GITHUB_REPO_BRANCH
RUN apk update && apk upgrade && \
  apk add --no-cache bash git openssh jq
RUN mkdir -p /usr/src/app
WORKDIR /usr/src/app
COPY $GITHUB_REPO_URL/package.json ./
COPY $GITHUB_REPO_URL/package-lock.json ./
ADD $GITHUB_REPO_URL/src src
ADD $GITHUB_REPO_URL/public public
ENV NODE_PATH src
RUN npm install && npm run test