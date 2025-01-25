# Dockerfile for Node API
FROM node:18

# Set the working directory in the container
WORKDIR /app

# Copy package.json and package-lock.json
COPY package*.json ./

# Install dependencies
RUN npm install

# Download the wait-for-it.sh script
RUN curl -sSL https://github.com/vishnubob/wait-for-it/blob/master/wait-for-it.sh -o /usr/local/bin/wait-for-it

# Make the script executable
RUN chmod +x /usr/local/bin/wait-for-it

# Copy the rest of the application code
COPY . .

# Expose the port the app runs on
EXPOSE 8706

# Wait for MongoDB and Redis before starting the Node.js app
CMD ["wait-for-it", "mongo:27017", "--", "wait-for-it", "redis:6379", "--", "npm", "start"]


