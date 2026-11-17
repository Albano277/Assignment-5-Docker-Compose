
# Use Node.js 18 with Alpine Linux as the base image.
FROM node:18-alpine

# Set the working directory inside the container.
WORKDIR /app

# Copy the package files needed to install dependencies.
COPY package*.json ./

# Install the Node.js dependencies.
RUN npm install

# Copy the remaining backend application files.
COPY . .

# Create a directory to store the SQLite database.
RUN mkdir -p /app/data

# Expose port 5000 for the backend application.
EXPOSE 5000

# Start the backend application.
CMD ["npm", "start"]
