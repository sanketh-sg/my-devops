# Pin specific version for stability
# Use slim for reduced image size
FROM node:20.14-bullseye-slim AS base

# Set NODE_ENV
ENV NODE_ENV=production

# Specify working directory other than /
WORKDIR /usr/src/app

# Install pnpm globally
RUN npm install -g pnpm

# Copy only files required to install dependencies (better layer caching)
COPY package*.json ./

# Install only production dependencies using pnpm
# Use cache mount to speed up install of existing dependencies
RUN --mount=type=cache,target=/usr/src/app/.pnpm-store \
  pnpm install --prod

# Use non-root user
# Use --chown on COPY commands to set file permissions
USER node

# Copy the healthcheck script
COPY --chown=node:node ./healthcheck/ .

# Copy remaining source code AFTER installing dependencies. 
# Again, copy only the necessary files
COPY --chown=node:node ./src/ .

# Indicate expected port
EXPOSE 3000

CMD [ "node", "index.js" ]
