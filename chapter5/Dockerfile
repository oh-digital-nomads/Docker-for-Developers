FROM ubuntu:bionic
RUN apt-get update && apt-get install curl sudo aptitude -y && \
    curl -sL https://deb.nodesource.com/setup_12.x | sudo -E bash -
RUN apt-get -qq update && \
    apt-get -qq install -y nodejs > /dev/null
RUN aptitude install -y npm > /dev/null
RUN mkdir -p /app/public /app/server
COPY src/package.json* /app
WORKDIR /app
RUN npm -s install
COPY src/.babelrc \
     src/.env \
     src/.nodemonrc.json \
     /app/
COPY src/public/ /app/public/
COPY src/server/ /app/server/
EXPOSE 3000
ENTRYPOINT DEBUG='shipit-clicker:*' npm run dev
