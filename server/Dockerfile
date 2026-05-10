# Stage 1: Build stage
FROM node:18-alpine AS builder

# Set the working directory inside the container
WORKDIR /app

# Copy package files and install dependencies
COPY package*.json ./
RUN npm ci --only=production

# Copy rest of the application source code
COPY . .

# Stage 2: Production stage (smaller final image)
FROM node:18-alpine
WORKDIR /app
COPY --from=builder /app .

# Expose the port the app runs on
EXPOSE 3001

# Start the application (Updated to match your folder structure!)
CMD ["node", "index.js"]