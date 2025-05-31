# Use official Node.js image
FROM node:20-alpine

# Set working directory
WORKDIR /app

# Copy dependencies first (better cache)
COPY frontend/package*.json ./

# Install dependencies
RUN npm install

# Copy rest of the app
COPY frontend .

# Build the app
RUN npm run build

# Expose port for Next.js
EXPOSE 3000

# Start the app
CMD ["npm", "start"]
