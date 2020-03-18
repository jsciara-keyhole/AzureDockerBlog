# Stage 1 - the build process
FROM node:current-alpine AS builder
WORKDIR /usr/src/app
COPY package.json yarn.lock ./
RUN yarn
COPY . ./
RUN yarn build

# Stage 2 - the production environment
FROM node:current-alpine
RUN yarn global add serve
WORKDIR /app
COPY --from=builder /usr/src/app/build .
CMD ["serve", "-p", "80", "-s", "."]



# Stage 2 - the production environment
#FROM nginx:1.12-alpine
#COPY --from=build-deps /usr/src/app/build /usr/share/nginx/html
#EXPOSE 80
#CMD ["nginx", "-g", "daemon off;"]