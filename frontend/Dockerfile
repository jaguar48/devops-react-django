# FROM node:14.17.3

# WORKDIR /frontend

# COPY . .

# RUN npm install

# RUN npm run build


# FROM nginx:1.21.0-alpine as production
# ENV NODE_ENV production
# COPY --from=builder /frontend/build /usr/share/nginx/html
# COPY nginx.conf /etc/nginx/conf.d/default.conf
# EXPOSE 80
# CMD ["nginx", "-g", "daemon off;"]

FROM node:14.17.6-alpine as build
WORKDIR /frontend
COPY package.json ./
COPY ./ ./
RUN npm i
RUN npm run build

# production environment
FROM nginx:stable-alpine
COPY --from=build /frontend/build /usr/share/nginx/html
COPY nginx.conf /etc/nginx/conf.d/default.conf
EXPOSE 80
CMD ["nginx", "-g", "daemon off;"]