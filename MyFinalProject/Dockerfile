FROM --platform=linux/arm/v7 alpine:latest
# تثبيت المكتبات
RUN apk add --no-cache libstdc++ gcompat icu-libs
WORKDIR /app
# نسخ الملفات مباشرة
COPY publish_final/ .
ENV ASPNETCORE_URLS=http://+:8080
EXPOSE 8080
# سنقوم بتشغيل الملف مباشرة عند الانطلاق
ENTRYPOINT ["/app/MyApi"]
