# Build Stage
FROM gradle:8.7-jdk17 AS build

WORKDIR /app

COPY . .

RUN chmod +x gradlew

RUN ./gradlew jsBrowserProductionWebpack

# Runtime Stage
FROM nginx:alpine

COPY --from=build /app/composeApp/build/dist/js/productionExecutable/*.js /usr/share/nginx/html/

EXPOSE 80

CMD ["nginx", "-g", "daemon off;"]