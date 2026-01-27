# -------------------------------
# Stage 1: Build React frontend
# -------------------------------
FROM node:20-alpine AS builder
WORKDIR /app

# Copy dependency files
COPY package.json package-lock.json ./

# Install deps (skip Windows-only optional deps)
RUN npm install --omit=optional

# Copy source
COPY . .

# Build React app
RUN npm run build

# -------------------------------
# Stage 2: Serve with nginx
# -------------------------------
FROM nginx:alpine

# Create non-root user
RUN adduser -D appuser

# Copy build output
COPY --from=builder /app/build /usr/share/nginx/html

# Run as non-root
USER appuser

EXPOSE 80
CMD ["nginx", "-g", "daemon off;"]
