# Start from the official Alpine Linux base image
FROM alpine:latest AS builder

# Install necessary packages
RUN apk update && apk add --no-cache git go

# Set the Current Working Directory inside the container
WORKDIR /app

# Copy the source code into the container
COPY . .

# Build the Go app
RUN go build 

# Start a new stage from scratch
FROM alpine:latest

WORKDIR /app

# Copy the Pre-built binary file from the previous stage
COPY --from=builder /app/sping /app

EXPOSE 6924

# Use ENTRYPOINT to allow passing arguments to the command
ENTRYPOINT ["/app/sping"]

