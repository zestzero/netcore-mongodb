FROM microsoft/dotnet:sdk AS build-env
WORKDIR /app

# Copy everything and build
COPY . ./

RUN dotnet restore "./TestCasesApi.csproj"
RUN dotnet publish "TestCasesApi.csproj" -c Release -o out


FROM microsoft/dotnet:aspnetcore-runtime
WORKDIR /app
EXPOSE 80 443
COPY --from=build-env /app/out .
ENTRYPOINT ["dotnet", "TestCasesApi.dll"]
