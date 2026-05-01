FROM node:24-alpine  AS build 
WORKDIR  /app 
COPY  package.json package-lock.json  ./
RUN  npm install 
COPY .  .
RUN npm run lint && npm run build  

FROM httpd:latest

COPY --from=build /app/dist/  htdocs/

EXPOSE 80

CMD ["httpd", "-D", "FOREGROUND"]



