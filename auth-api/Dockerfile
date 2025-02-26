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
FROM alpine:latest

# Install necessary libraries
RUN apk --no-cache add ca-certificates

# Copy the compiled Go binary from the build stage
COPY --from=build /app/auth-api /usr/local/bin/

# Expose the app port
EXPOSE 8080

# Start the app
CMD ["auth-api"]
