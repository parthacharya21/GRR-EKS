# Use the official Nginx base image
FROM nginx:alpine

# Install tools like ping or netstat
RUN apk add --no-cache iputils net-tools

# Rename the ping process to 'evil'
RUN mv /bin/ping /bin/evil

# Start Nginx and also run the 'evil' process
CMD ["sh", "-c", "nginx & /bin/evil localhost & tail -f /dev/null"]