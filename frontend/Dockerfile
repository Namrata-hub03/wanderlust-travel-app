# stage 1 
FROM node:21 AS frontend-builder

# set the work dir to /app
WORKDIR /app

# Copy the package.json and package-lock.json for dependency installation
COPY package*.json ./

#install dependencies
RUN npm install

# copy the rest of the code
COPY . .

# Stage 2
FROM node:21-slim

# set the work dir to /app
WORKDIR /app

# copy built assets and dependencies from frontend-builder stage
COPY --from=frontend-builder /app .

# copy the .env.sample file to .env.local
COPY .env.sample .env.local

# Expose port 5173 for the node.js appl
EXPOSE 5173

# Define the default command to run the appl in dev
CMD ["npm", "run", "dev", "--", "--host"]

