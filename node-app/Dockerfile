# Stage 1: Build
FROM node:latest AS builder

# Setting the working directory to /app
WORKDIR /app

# Copying package.json and package-lock.json to /app
COPY package.json package-lock.json ./

# Installing npm dependencies
RUN npm install

# Copying the rest of the application files
COPY . .

# Stage 2: Production for ARM64
FROM --platform=linux/arm64 node:alpine

# Setting the working directory to /app
WORKDIR /app

# Copying only the necessary files from the builder stage
COPY --from=builder /app /app

# Exposing the web application on port 3000
EXPOSE 3000

# Running the service
CMD ["node", "index.js"]
