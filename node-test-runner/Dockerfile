FROM node:10.4.0-alpine

ENV GITHUB_CLONE_URL ${GITHUB_CLONE_URL:-https://github.com/dictyBase/dicty-frontpage.git}
ENV GITHUB_REPO_NAME ${GITHUB_REPO_NAME:-dicty-frontpage}
ENV CLIENT_KEYS ${CLIENT_KEYS:-https://raw.githubusercontent.com/dictybase-playground/client-keys/2.0.0/clientConfig.eric.js}

RUN apk update && apk upgrade && \
  apk add --no-cache bash git openssh jq
RUN git clone $GITHUB_CLONE_URL && cd $GITHUB_REPO_NAME

WORKDIR /$GITHUB_REPO_NAME

# overwrite the client key file
ADD $CLIENT_KEYS src/utils/clientConfig.js

# ENV CI is required to run tests without interactive mode
# https://facebook.github.io/create-react-app/docs/running-tests#on-your-own-environment
ENV CI true

RUN npm install

CMD ["npm"]