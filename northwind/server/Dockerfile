# DB_USER DB_PASSWORD
# DONT ADD CONFIG DIRECTY
# nwapp
FROM node:latest
ENV APP_ROOT=/app APP_PORT=3000
ENV DB_USER=root DB_PASSWORD=changeit

# create APP_ROOT and cd in
WORKDIR ${APP_ROOT}

# copy the files and directory into
ADD main.js .
ADD package.json .
ADD package-lock.json .

ADD public public
ADD views views
ADD config config

RUN npm install

# health check
HEALTHCHECK --interval=30s --timeout=5s --start-period=5s --retries=3 \ 
    CMD curl -s -f http://localhost:${APP_ROOT}/health || exit 1

EXPOSE ${APP_PORT}

ENTRYPOINT ["node", "main.js"]


