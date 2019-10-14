FROM mcr.microsoft.com/dotnet/core/sdk:3.0 AS build
WORKDIR /app

# copy csproj and restore as distinct layers
COPY *.sln .
COPY tests/ ./tests/
COPY src/Conduit/*.csproj ./src/Conduit/
RUN dotnet restore

# copy everything else and build app
COPY src/Conduit/. ./src/Conduit/
WORKDIR /app/src/Conduit
RUN dotnet publish -c Release -o out


FROM mcr.microsoft.com/dotnet/core/aspnet:2.2 AS runtime
WORKDIR /app
COPY --from=build /app/src/Conduit/out ./
EXPOSE 5000
ENTRYPOINT ["dotnet", "Conduit.dll"]