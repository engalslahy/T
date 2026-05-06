# مرحلة البناء باستخدام SDK 10
FROM mcr.microsoft.com/dotnet/sdk:10.0-preview-alpine AS build
WORKDIR /src

# نسخ ملفات المشروع وعمل Restore
COPY ["MyApi/MyApi.csproj", "MyApi/"]
RUN dotnet restore "MyApi/MyApi.csproj" -r linux-musl-arm

# نسخ بقية الملفات وبناء التطبيق
COPY . .
WORKDIR "/src/MyApi"

# النشر كملف واحد مستقل تماماً لـ ARM 32-bit (للميكروتك)
RUN dotnet publish "MyApi.csproj" -c Release -o /app/publish     -r linux-musl-arm     --self-contained true     -p:PublishSingleFile=true     -p:PublishTrimmed=true

# مرحلة التشغيل النهائية (Alpine Slim)
FROM alpine:latest
# إضافة المكتبات الضرورية لتشغيل دوت نت (Self-contained)
RUN apk add --no-cache libstdc++ gcompat icu-libs
WORKDIR /app
COPY --from=build /app/publish .

# إعدادات الشبكة
ENV ASPNETCORE_URLS=http://+:8080
EXPOSE 8080

ENTRYPOINT ["./MyApi"]
