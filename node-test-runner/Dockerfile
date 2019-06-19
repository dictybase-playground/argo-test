FROM node:10.4.0-alpine
ARG clone_url
ENV GITHUB_CLONE_URL ${clone_url:-https://github.com/dictyBase/dicty-frontpage.git}
ARG name
ENV GITHUB_REPO_NAME ${name:-dicty-frontpage}
RUN apk update && apk upgrade && \
  apk add --no-cache bash git openssh jq
RUN mkdir -p /usr/src/app
WORKDIR /usr/src/app
RUN git clone $GITHUB_CLONE_URL && cd $GITHUB_REPO_NAME
COPY package*.json ./
ADD src src
ADD public public
ENV NODE_PATH src
RUN npm install && npm run test