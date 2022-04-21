## Build and Run container

1. Navigate to the folder where the Dockerfile is stored
2. Run ```docker build -t angular-container:1.0 .```
3. Search ImageID by running ```docker images```
4. Run ```docker run -p 80:80 469b3a773ed7```

## Dockerfile example
```
FROM node:lts as node

RUN npm install -g @angular/cli

WORKDIR /usr/src/app
COPY src/TeamHub.UI/ ./my-app/

WORKDIR /usr/src/app/my-app
RUN npm install
RUN npm run build

FROM nginx:alpine
COPY --from=node /usr/src/app/my-app/dist/team-hub.ui /usr/share/nginx/html
```