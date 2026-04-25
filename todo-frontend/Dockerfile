# Stage 1: Build
FROM node:20-alpine as build

WORKDIR /app

COPY package*.json ./
RUN npm install

COPY . .

# Inject env at build time for prod
ARG REACT_APP_API_BASE_URL
ARG REACT_APP_API_BASE_URL2

ENV REACT_APP_API_BASE_URL=$REACT_APP_API_BASE_URL
ENV REACT_APP_API_BASE_URL2=$REACT_APP_API_BASE_URL2

RUN npm run build


# Stage 2: Serve
FROM nginx:alpine

COPY --from=build /app/build /usr/share/nginx/html

EXPOSE 80

CMD ["nginx", "-g", "daemon off;"]