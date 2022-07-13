## Create a Web Api project
    In VS code press ctrl + f5 to run the app
## Prerequisites

.Net 6.0 SDK
C#

## Create a web project

    dotnet new webapi -o TodoApi
    cd TodoApi
    dotnet add package Microsoft.EntityFrameworkCore.InMemory
    code -r ../TodoApi

    This commands create a web Api Project
    And add NuGet package

## Trust HTTPS development certificated on Linux

    dotnet dev-certs https
    sudo -E dotnet dev-certs https -ep /usr/local/share/ca-certificates/aspnet/https.crt --format PEM
    sudo update-ca-certificates

    https://aka.ms/dev-certs-trust

    Trust Certificates in Edge or Chrome
        sudo apt install libnss3-tools
        dotnet dev-certs https
        sudo -E dotnet dev-certs https -ep /usr/local/share/ca-certificates/aspnet/https.crt --format PEM
        certutil -d sql:$HOME/.pki/nssdb -A -t "C,," -n localhost -i /usr/local/share/ca-certificates/aspnet/https.crt

    Trust Certificates in Firefox
        dotnet dev-certs https
        sudo -E dotnet dev-certs https -ep /usr/local/share/ca-certificates/aspnet/https.crt --format PEM

        cat <<EOF | sudo tee /usr/lib/firefox/distribution/policies.json
            {
                "policies": {
                    "Certificates": {
                        "Install": [
                            "/usr/local/share/ca-certificates/aspnet/https.crt"
                        ]
                    }
                }
            }
        EOF


## The Swagger Page 
    The Swagger page /swagger/index.html is displayed. Select GET > Try it out > Execute. The page displays:

        The Curl command to test the WeatherForecast API.
        The URL to test the WeatherForecast API.
        The response code, body, and headers.
        A drop down list box with media types and the example value and schema.

## Configure launchUrl

    In Propeties/launchSettings.json configure url how "api/todoitems".

## Scaffold a controllers

    Run the commands

        dotnet add package Microsoft.VisualStudio.Web.CodeGeneration.Design
        dotnet add package Microsoft.EntityFrameworkCore.Design
        dotnet add package Microsoft.EntityFrameworkCore.SqlServer
        dotnet tool install -g dotnet-aspnet-codegenerator
        dotnet aspnet-codegenerator controller -name TodoItemsController -async -api -m TodoItem -dc TodoContext -outDir Controllers

    This commands add packages required for scaffolding
    Intall the scaffolding engine "dotnet-aspnet-codegenerator"
    And add the TodoItemsController

## Install http-repl
    dotnet tool install -g Microsoft.dotnet-httprepl

## Test PostTodoItem

    POST - http://localhost:5004/api/todoitems/
    {
        "id": 1,
        "name": "walk dog",
        "isComplete": true
    }

    And test the GET method ../api/tooditems/:id
    And test the PUT method ../api/tooditems/:id
