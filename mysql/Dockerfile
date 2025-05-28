FROM alpine:latest AS builder
WORKDIR /app
COPY mysql-init /app
RUN apk add --no-cache openssl

# Base image for the final MongoDB image
FROM mysql:8.0

#Copy initialization scripts from the build stage
COPY --from=builder /app /docker-entrypoint-initdb.d

# Set mySQL environment variables 
ENV MYSQL_ROOT_PASSWORD=admin

#Expose the MongoDB port
EXPOSE 3306