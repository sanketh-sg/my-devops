# syntax=docker/dockerfile:1.5

FROM node:20.14-bullseye-slim AS build

# Specify working directory other than /
WORKDIR /usr/src/app

# Install pnpm globally
RUN npm install -g pnpm

# Copy only files required to install dependencies (better layer caching)
COPY package*.json ./

# Use cache mount to speed up install of existing dependencies
RUN --mount=type=cache,target=/usr/src/app/.pnpm-store \
  pnpm install

# Copy the rest of the application code
COPY . .

# Build the application
RUN pnpm run build

# Use separate stage for deployable image
FROM nginxinc/nginx-unprivileged:1.23-alpine-perl

# Use COPY --link to avoid breaking cache if we change the second stage base image
COPY --link nginx.conf /etc/nginx/conf.d/default.conf

# Copy the built application from the first stage
COPY --link --from=build /usr/src/app/dist/ /usr/share/nginx/html

# Expose the expected port
EXPOSE 8080
