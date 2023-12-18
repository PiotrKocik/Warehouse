FROM mcr.microsoft.com/dotnet/sdk:7.0 AS build
WORKDIR /app
COPY . .
RUN dotnet publish ./src/Warehouse.Domain.Api -c release -o publish 

FROM mcr.microsoft.com/dotnet/aspnet:7.0
WORKDIR /app
COPY --from=build /app/publish .
ENV ASPNET_URLS http://*:80
ENV ASPNET_ENVIRONMENT docker
ENTRYPOINT ["dotnet", "Warehouse.Domain.Api.dll"]