# -------------------------------
# Stage 1: Build React frontend
# -------------------------------
FROM node:20-alpine AS builder
WORKDIR /app

# Copy both package.json and package-lock.json
COPY package.json package-lock.json ./
RUN npm config set optional=false

# Install exact dependencies from lock file
RUN npm install --omit=optional


# Copy all frontend code
COPY . .

# Build React app
RUN npm run build

# -------------------------------
# Stage 2: Serve with nginx
# -------------------------------
FROM nginx:alpine

# Create a non-root user
RUN adduser -D appuser

# Copy build output from builder stage
COPY --from=builder /app/build /usr/share/nginx/html

# Use non-root user
USER appuser

# Expose port 80
EXPOSE 80

# Start nginx
CMD ["nginx", "-g", "daemon off;"]
