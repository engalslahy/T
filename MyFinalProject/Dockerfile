FROM --platform=linux/arm/v7 alpine:latest
# تثبيت المكتبات الضرورية لتشغيل دوت نت المستقل
RUN apk add --no-cache libstdc++ gcompat icu-libs
WORKDIR /app
# نسخ الملفات التي بنيناها في خطوة publish
COPY publish/ .

ENV ASPNETCORE_URLS=http://+:8080
EXPOSE 8080

ENTRYPOINT ["./MyApi"]
