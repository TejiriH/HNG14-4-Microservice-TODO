# Step 1: Build the Go app
FROM golang:1.21 AS build

# Set the working directory
WORKDIR /app

# Copy the Go module files and install dependencies
COPY go.mod go.sum ./
RUN go mod tidy

# Copy the source code
COPY . .

# Build the app
RUN go build -o auth-api .

# Step 2: Run the app
FROM debian:latest

# Install necessary libraries
RUN apt-get update && apt-get install -y ca-certificates

# Copy the compiled Go binary from the build stage
COPY --from=build /app/auth-api /usr/local/bin/

# Expose the app port
EXPOSE 8081

# Set the environment variable AUTH_API_PORT
ENV AUTH_API_PORT 8081

# Start the app
CMD ["/usr/local/bin/auth-api"]
