# Base image
FROM node:18

# Create app directory
WORKDIR /usr/src/app

# A wildcard is used to ensure both package.json AND package-lock.json are copied
COPY package*.json yarn.lock tsconfig.json ./

# Install app dependencies
RUN npm install

# Bundle app source
COPY src src

# Creates a "dist" folder with the production build
RUN npm run build && rm -rf src

# Copy the dependencies into a Slim Node docker image
FROM node:18-slim

# Install app dependencies
COPY --from=0 /usr/src/app/node_modules /usr/src/app/node_modules
COPY --from=0 /usr/src/app/dist /usr/src/app/dist

WORKDIR /usr/src/app

ENV NODE_ENV production
ENV PORT 3000

#expose port 3000
EXPOSE 3000

# Start the server using the production build
CMD [ "node", "dist/main.js" ]
