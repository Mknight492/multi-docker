#build react with node
FROM node:alpine 
WORKDIR '/app'
COPY package*.json ./
RUN npm install
COPY . .
RUN npm run build

#serve static output from nginx
FROM nginx
EXPOSE 3000
COPY ./nginx/default.conf /etc/nginx.conf.d/default.conf
COPY --from=0 /app/build /usr/share/nginx/html

#aws will fail with named builders