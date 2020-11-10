FROM node:alpine as builder
WORKDIR '/app'
COPY package.json .
RUN npm install
COPY . .
RUN npm run build

FROM nginx
# must expose port for AWS elastic beanstalk
EXPOSE 3000
# from a different phase(phase 0) 
# what do you want to copy 
# and where do you want to copy it to
COPY ./nginx/default.conf /etc/nginx/conf.d/default.conf
COPY --from=builder /app/build /usr/share/html