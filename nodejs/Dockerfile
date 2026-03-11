# Use an official Node.js runtime as the base image
# Must begin with FROM instruction - to specify the base image
FROM node:25.8

# Set the working directory in the container
COPY package.json /app/
COPY server.js /app/

WORKDIR /app

# RUN instruction to execute commands in a shell inside the container during the build process. It is used to install dependencies, set up the environment, and perform other tasks needed to prepare the image for running the application.
RUN npm install

# CMD instruction to specify the default command to run when starting a container from the image. It is used to define the command that will be executed when the container starts, such as running the application or starting a server. Only one CMD instruction is allowed in a Dockerfile, and if multiple CMD instructions are present, only the last one will take effect.
CMD ["node", "server.js"]