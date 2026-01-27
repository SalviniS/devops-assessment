
# -------------------------------
# Stage 1: Build React frontend
# -------------------------------
FROM node:20-alpine AS builder
WORKDIR /app

# Install build tools for optional native deps
RUN apk add --no-cache python3 g++ make git bash

# Copy dependency files
COPY package.json package-lock.json ./

# Install deps
RUN npm ci

# Copy source
COPY . .

# Build React app
RUN npm run build

# -------------------------------
# Stage 2: Serve with nginx
# -------------------------------
FROM nginx:alpine

# Copy build output
COPY --from=builder /app/dist /usr/share/nginx/html


# Create directories (optional)
RUN mkdir -p /var/cache/nginx /var/run \
    && chmod -R 777 /var/cache/nginx /var/run /usr/share/nginx/html

# Expose port
EXPOSE 80

# Use non-root user
USER nginx

# Start Nginx
CMD ["nginx", "-g", "daemon off;"]

