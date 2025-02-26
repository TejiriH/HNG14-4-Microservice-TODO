# Step 1: Build the Node.js app
FROM node:14 AS build

# Set the working directory
WORKDIR /app

# Copy the package.json and install dependencies
COPY package.json ./
RUN npm install

# Copy the rest of the application files
COPY . .

# Expose the required port
EXPOSE 8081

# Run the app
CMD ["npm", "start"]
