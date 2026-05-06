FROM --platform=linux/arm/v7 alpine:latest
RUN apk add --no-cache libstdc++ gcompat icu-libs
WORKDIR /app
# نسخ محتويات مجلد publish إلى المجلد الحالي /app
COPY publish/ .
# إعطاء صلاحيات تنفيذ للملف
RUN chmod +x /app/MyApi

ENV ASPNETCORE_URLS=http://+:8080
EXPOSE 8080
# التأكد من المسار الكامل للتشغيل
ENTRYPOINT ["/app/MyApi"]
