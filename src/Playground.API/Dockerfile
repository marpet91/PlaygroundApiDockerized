FROM mcr.microsoft.com/dotnet/aspnet:6.0 AS base
WORKDIR /app
EXPOSE 80
EXPOSE 443

FROM mcr.microsoft.com/dotnet/sdk:6.0 AS build
WORKDIR /src
COPY ["src/Playground.API/Playground.API.csproj", "Playground.API/"]
COPY ["src/Playground.Core/Playground.Core.csproj", "Playground.Core/"]
RUN dotnet restore "src/Playground.API/Playground.API.csproj"
COPY . .
WORKDIR "/src/Playground.API"
RUN dotnet build "Playground.API.csproj" -c Release -o /app/build

FROM build AS publish
RUN dotnet publish "Playground.API.csproj" -c Release -o /app/publish

FROM base AS final
WORKDIR /app
COPY --from=publish /app/publish .
ENTRYPOINT ["dotnet", "Playground.API.dll"]
