
# Base image
FROM node:14 as builder
# Set working directory
WORKDIR /app
# Copy package.json and package-lock.json
COPY package*.json ./
# Install dependencies
RUN npm install
# Install elastic-apm-node globally
RUN npm install @elastic/apm-rum --save
# Copy project files
COPY . .
# Build the frontend
RUN npm run build
# Production-ready image
FROM nginx:1.19-alpine
COPY --from=builder /app/build /usr/share/nginx/html
COPY conf/nginx.conf /etc/nginx/conf.d/default.conf
# Expose port 80
EXPOSE 80
# Start Nginx
CMD ["nginx", "-g", "daemon off;"]
