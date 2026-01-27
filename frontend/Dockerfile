# -------------------------------
# Stage 1: Build Vite React frontend
# -------------------------------
FROM node:20-alpine AS builder
WORKDIR /app

# Install build tools (safe to keep)
RUN apk add --no-cache python3 g++ make git bash

# Copy dependency files
COPY package.json package-lock.json ./

# Install dependencies
RUN npm ci

# Copy source code
COPY . .

# Build Vite app (creates /app/dist)
RUN npm run build

# -------------------------------
# Stage 2: Serve with nginx
# -------------------------------
FROM nginx:alpine

# Copy Vite build output
COPY --from=builder /app/dist /usr/share/nginx/html

# Expose port
EXPOSE 80

# Use nginx default user
USER nginx

# Start nginx
CMD ["nginx", "-g", "daemon off;"]
