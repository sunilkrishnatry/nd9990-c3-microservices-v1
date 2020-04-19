## Build
FROM agileek/ionic-framework AS ionic
##FROM agileek/ionic-framework AS ionic
# Create the application directory
WORKDIR /usr/src/app

# Install the application dependencies
# We can use wildcard to ensure both package.json AND package-lock.json are considered
# where available (npm@5+)
#ENV PATH /usr/local/bin/python3.7:$PATH

COPY package*.json ./
RUN npm ci
# Bundle app source
COPY . .

#SRUN apt-get update && apt-get install -y build-essential python-dev python-pip
#RUN apt-get install python3.
RUN ionic build

## Run 
FROM nginx:alpine
#COPY www /usr/share/nginx/html
COPY --from=ionic /usr/src/app/www /usr/share/nginx/html