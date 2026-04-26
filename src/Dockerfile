FROM mcr.microsoft.com/dotnet/sdk:10.0 AS build

WORKDIR /app

COPY ./cart-service/src /app/src
COPY ./pb /app/pb

WORKDIR /app/src

RUN dotnet publish ./cart.csproj -c Release -o /out

FROM mcr.microsoft.com/dotnet/runtime-deps:10.0

WORKDIR /app

COPY --from=build /out .

ENV DOTNET_HOSTBUILDER__RELOADCONFIGONCHANGE=false

EXPOSE 8080

ENTRYPOINT ["./cart"]