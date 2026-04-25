# Use official node image
FROM node:20-alpine

# Create app directory
WORKDIR /app

# Copy package files
COPY package*.json ./

# Install dependencies
RUN npm install

# Copy project files
COPY . .

# Expose backend port
EXPOSE 5001

# Start server
CMD ["npm", "start"]