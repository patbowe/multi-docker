FROM node:alpine as builder
WORKDIR '/app'
COPY ./package.json ./
COPY ./default.conf ./
COPY ../nginx/default.conf ./
RUN ls -l ../nginx
#RUN npm install
COPY . .
RUN npm run build

FROM nginx
EXPOSE 3000
RUN pwd
RUN ls /tmp
COPY ./nginx/default.conf /etc/nginx/conf.d/default.conf
COPY --from=builder /app/build /usr/share/nginx/html
