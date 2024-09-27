FROM mcr.microsoft.com/dotnet/core/sdk:3.1 AS build
WORKDIR /app

COPY src/Worker/Worker.csproj ./
RUN dotnet restore

COPY src/Worker ./


RUN dotnet publish -c Release -o /out Worker.csproj


FROM mcr.microsoft.com/dotnet/core/runtime:3.1 AS runtime
WORKDIR /app

# Copy the published output from the build stage
COPY --from=build /out .

CMD ["dotnet", "Worker.dll"]

