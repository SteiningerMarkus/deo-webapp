FROM mcr.microsoft.com/dotnet/sdk:8.0-alpine3.20 AS build-stage
WORKDIR /build
COPY . .
RUN dotnet publish

FROM mcr.microsoft.com/dotnet/sdk:8.0-alpine3.20
WORKDIR /app
COPY --from=build-stage /build/bin/Release/net8.0/publish .
ENV ASPNETCORE_URLS=http://*:2000
ENTRYPOINT ["/app/Deo.Frontend"]

EXPOSE 2000/tcp