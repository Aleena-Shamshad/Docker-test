FROM node:18 AS build
WORKDIR /app
COPY package*.json ./
RUN npm install
RUN npm install web-vitals
COPY . .
RUN npm run build
FROM nginx:stable-alpine AS production
COPY --from=build /app/build /usr/share/nginx/html
EXPOSE 80
CMD ["nginx", "-g", "daemon off;"]

#EXPOSE 3000
#CMD ["npm", "start"]
