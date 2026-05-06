FROM --platform=linux/arm/v7 alpine:latest
RUN apk add --no-cache libstdc++ gcompat icu-libs
WORKDIR /app
COPY . .
ENV ASPNETCORE_URLS=http://+:8080
EXPOSE 8080
ENTRYPOINT ["./MyApi"]
