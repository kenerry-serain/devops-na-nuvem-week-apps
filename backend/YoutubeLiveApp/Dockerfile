FROM mcr.microsoft.com/dotnet/sdk:7.0-alpine as build
WORKDIR /nsse-backend
COPY . .
RUN dotnet publish /nsse-backend/YoutubeLiveApp.csproj \
    -c Release \
    -o publish

FROM mcr.microsoft.com/dotnet/aspnet:7.0-alpine
WORKDIR /nsse-backend
COPY --from=build /nsse-backend/publish .
EXPOSE 80

ENTRYPOINT ["dotnet", "/nsse-backend/YoutubeLiveApp.dll"]

