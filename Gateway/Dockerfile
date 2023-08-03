# Use a base image
FROM mcr.microsoft.com/dotnet/aspnet:7.0 AS base
WORKDIR /app
EXPOSE 80

# Build the application
FROM mcr.microsoft.com/dotnet/sdk:7.0 AS build
WORKDIR /src
COPY ["Gateway.csproj", "./"]
RUN dotnet restore "./Gateway.csproj"
COPY . .
WORKDIR "/src/."
RUN dotnet build "Gateway.csproj" -c Release -o /app/build

# Publish the application
FROM build AS publish
RUN dotnet publish "Gateway.csproj" -c Release -o /app/publish

# Create the final image
FROM base AS final
WORKDIR /app
COPY --from=publish /app/publish .
ENTRYPOINT ["dotnet", "Gateway.dll"]