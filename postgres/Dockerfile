FROM alpine:latest AS builder
WORKDIR /app
COPY postgres-init ./
RUN apk add --no-cache openssl

# Base image for the final MongoDB image
FROM postgres:latest

#Copy initialization scripts from the build stage
COPY --from=builder /app /docker-entrypoint-initdb.d

# Set PostgreSQL environment variables 
ENV POSTGRES_USER=postgres
ENV POSTGRES_PASSWORD=admin
ENV POSTGRES_DB=eCommerceUsers

#Expose the MongoDB port
EXPOSE 5432