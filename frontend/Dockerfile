
# Stage 1: Build the React application using Node.js 18.
FROM node:18-alpine AS builder

# Set the working directory inside the container.
WORKDIR /app

# Copy the package files needed for dependency installation.
COPY package*.json ./

# Install the frontend dependencies.
RUN npm install

# Set the backend API URL during the build.
ARG VITE_API_URL
ENV VITE_API_URL=$VITE_API_URL

# Copy the remaining frontend application files.
COPY . .



# Build the production version of the React application.
RUN npm run build

# Stage 2: Use nginx to serve the production application.
FROM nginx:alpine

# Copy the built application from the first stage into nginx.
COPY --from=builder /app/dist /usr/share/nginx/html

# Expose port 80 for the web server.
EXPOSE 80

# Start nginx and keep it running in the foreground.
CMD ["nginx", "-g", "daemon off;"]
