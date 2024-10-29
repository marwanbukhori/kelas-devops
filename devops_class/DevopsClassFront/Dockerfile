# Stage 1
FROM node:20 as build

#set the working directory to /app
WORKDIR /app

# copy the package.json and package-lock.json files to the working directory
COPY package*.json ./

RUN npm install

#  copies all the files from your local directory into the container's /app directory.
COPY . .

# run the build script
RUN npm run build

# Stage 2
FROM httpd:2.4

COPY --from=build /app/dist/ /usr/local/apache2/htdocs/

# Configure Apache
RUN echo "ServerName localhost" >> /usr/local/apache2/conf/httpd.conf

EXPOSE 8001
