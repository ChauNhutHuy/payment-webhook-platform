# Stage 1: Build & Publish (dung SDK day du de bien dich C#)
FROM mcr.microsoft.com/dotnet/sdk:10.0 AS build
WORKDIR /src

# Copy cac file .csproj truoc de tan dung layer cache cho buoc dotnet restore
COPY src/PayFlow.Domain/PayFlow.Domain.csproj src/PayFlow.Domain/
COPY src/PayFlow.Application/PayFlow.Application.csproj src/PayFlow.Application/
COPY src/PayFlow.Infrastructure/PayFlow.Infrastructure.csproj src/PayFlow.Infrastructure/
COPY src/PayFlow.Api/PayFlow.Api.csproj src/PayFlow.Api/

RUN dotnet restore src/PayFlow.Api/PayFlow.Api.csproj

# Copy toan bo source code va publish ra /app/publish
COPY src/ src/
RUN dotnet publish src/PayFlow.Api/PayFlow.Api.csproj -c Release -o /app/publish --no-restore

# Stage 2: Runtime (chi dung ASP.NET Runtime gon nhe, khong chua SDK hay file .cs)
FROM mcr.microsoft.com/dotnet/aspnet:10.0 AS final
WORKDIR /app

# Chay bang user non-root 'app' co san trong image .NET cua Microsoft
USER app

EXPOSE 8080

COPY --from=build /app/publish .
ENTRYPOINT ["dotnet", "PayFlow.Api.dll"]
