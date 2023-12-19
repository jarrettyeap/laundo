# Base image
FROM node:latest as build

# Create `app` directory
WORKDIR /usr/src/app

RUN npm install -g pnpm

COPY pnpm-lock.yaml ./
COPY package.json ./
RUN pnpm install

COPY . .

RUN

FROM node:alpine
WORKDIR /usr/src/app
COPY --from=build /usr/src/app/dist/apps/[app-name] ./dist
COPY package*.json ./
RUN npm install --only=production
EXPOSE 3000
CMD ["node", "dist/main"]
