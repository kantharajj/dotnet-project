FROM mcr.microsoft.com/dotnet/core/sdk:2.1 as dev
RUN mkdir /work/
WORKDIR /work
COPY ./src/work.csproj /work/work.csproj
RUN dotnet restore

COPY ./src /work
RUN mkdir /out/
RUN dotnet publish --no-restore --output /out/ --configuration Release

FROM mcr.microsoft.com/dotnet/core/aspnet:2.1 as prod

RUN mkdir /app/
WORKDIR /app/

COPY --from=dev /out/ /app/
RUN chmod +x /app/
CMD dotnet work.dll
