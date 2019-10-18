FROM mcr.microsoft.com/dotnet/core/aspnet:3.0-stretch-slim AS base
WORKDIR /app
EXPOSE 80
EXPOSE 443

FROM mcr.microsoft.com/dotnet/core/sdk:3.0-stretch AS build
WORKDIR /src
COPY ["demodotnetcore/demodotnetcore.csproj", "demodotnetcore/"]
RUN dotnet restore "demodotnetcore/demodotnetcore.csproj"
COPY . .
WORKDIR "/src/demodotnetcore"
RUN dotnet build "demodotnetcore.csproj" -c Release -o /app

FROM build AS publish
RUN dotnet publish "demodotnetcore.csproj" -c Release -o /app

FROM base AS final
WORKDIR /app
COPY --from=publish /app .
ENTRYPOINT ["dotnet", "demodotnetcore.dll"]