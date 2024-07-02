FROM mcr.microsoft.com/dotnet/aspnet:7.0-alpine AS base
WORKDIR /app
EXPOSE 80
EXPOSE 443

FROM mcr.microsoft.com/dotnet/sdk:7.0-alpine AS build
WORKDIR /src
COPY ["SubscribeMessage/SubscribeMessage.csproj", "SubscribeMessage/"]
RUN dotnet restore "SubscribeMessage/SubscribeMessage.csproj"
COPY . .
WORKDIR "/src/SubscribeMessage"
RUN dotnet build "SubscribeMessage.csproj" -c Release -o /app/build

FROM build AS publish
RUN dotnet publish "SubscribeMessage.csproj" -c Release -o /app/publish /p:UseAppHost=false

FROM base AS final
WORKDIR /app
COPY --from=publish /app/publish .
ENTRYPOINT ["dotnet", "SubscribeMessage.dll"]