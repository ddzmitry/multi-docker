# All refered to builder phase
FROM node:alpine as builder
WORKDIR '/app'
COPY package.json .
RUN npm install
COPY  . .
RUN npm run build

FROM nginx
EXPOSE 3000
# Copy from builder phase
# https://hub.docker.com/_/nginx
COPY ./nginx/default.conf /etc/nginx/conf.d/default.conf
COPY --from=builder /app/build /usr/share/nginx/html
# Default command will start nginx for us 
