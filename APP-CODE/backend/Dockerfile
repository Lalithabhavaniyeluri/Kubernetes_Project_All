# Use an official Node.js runtime as a base image
FROM node:14

# Set working directory
WORKDIR /app

# Copy package.json and package-lock.json
COPY package*.json ./

# Install dependencies
RUN npm install

# installing elastic-apm-agent
RUN npm install elastic-apm-node --save

# Install MySQL client library
RUN npm install mysql

# Copy project files
COPY . .

# Expose port 5000
EXPOSE 5000

# Start the backend server
CMD ["node", "server.js"]

