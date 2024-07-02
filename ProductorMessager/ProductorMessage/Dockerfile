FROM mcr.microsoft.com/dotnet/aspnet:7.0-alpine AS base
WORKDIR /app
EXPOSE 80
EXPOSE 443

FROM mcr.microsoft.com/dotnet/sdk:7.0-alpine AS build
WORKDIR /src
COPY ["ProductorMessage/ProductorMessage.csproj", "ProductorMessage/"]
RUN dotnet restore "ProductorMessage/ProductorMessage.csproj"
COPY . .
WORKDIR "/src/ProductorMessage"
RUN dotnet build "ProductorMessage.csproj" -c Release -o /app/build

FROM build AS publish
RUN dotnet publish "ProductorMessage.csproj" -c Release -o /app/publish /p:UseAppHost=false

FROM base AS final
WORKDIR /app
COPY --from=publish /app/publish .
ENTRYPOINT ["dotnet", "ProductorMessage.dll"]