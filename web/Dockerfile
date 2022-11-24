FROM node
ENV CHOKIDAR_USEPOLLING=true
RUN apt-get update && apt-get install -y iputils-ping
WORKDIR /app/
COPY package.json .
COPY package-lock.json .
RUN npm install
COPY . .
EXPOSE 3000
CMD [ "npm", "start" ]
