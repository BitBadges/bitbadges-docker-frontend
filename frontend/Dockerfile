FROM node:18-alpine3.17 as builder

#Set up working directory and navigate
WORKDIR /home
ARG ACCESS_TOKEN
ARG GITHUB_USERNAME

#Install Git and SSH
RUN apk update && apk add git openssh curl make wget bash


#Clone the private repository with Git credentials
#Run git clone with trevormil:ACCESS_TOKEN
RUN git clone https://$GITHUB_USERNAME:$ACCESS_TOKEN@github.com/bitbadges/bitbadges-frontend.git


WORKDIR /home/bitbadges-frontend
RUN npm install -g npm

RUN npm install

COPY frontend.env .
RUN mv frontend.env .env

RUN npm run build




# Define an argument for the .env file
# ARG ENV_FILE

# COPY .env .
# ENV $(cat $ENV_FILE | xargs)
RUN npm install -g pm2



# #Expose relevant ports
EXPOSE 3000

# EXPOSE 80



# CMD ["pm2-runtime", "start", "npm", "--name", "next-app", "--", "start"]
CMD ["npm", "run", "start"]


# CMD ["npm", "run", "start"]

# RUN systemctl status nginx
# RUN npm install -g pm2
# RUN pm2 start --name=website npm -- start
# RUN pm2 startup systemd && exit 1
# # TODO: watever is at end
# RUN systemctl status pm2-bob
# RUN cd /etc/nginx/sites-available




# # Run npm run setup and npm run indexer
# CMD ["npm", "run", "start"]

# commands
# docker build -t bitbadges .
# docker run -it bitbadges