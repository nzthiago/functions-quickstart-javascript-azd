---
name: "Azure Functions JavaScript HTTP Trigger using AZD"
description: This repository contains a Azure Functions HTTP trigger quickstart written in JavaScript and deployed to Azure using Azure Developer CLI (AZD). This sample uses manaaged identity and a virtual network to insure it is secure by default.
page_type: sample
languages:
- nodejs
- JavaScript
products:
- azure
- azure-functions
- entra-id
urlFragment: functions-quickstart-javascript-azd
---

# Azure Functions JavaScript HTTP Trigger using AZD

This repository contains a Azure Functions HTTP trigger quickstart written in JavaScript and deployed to Azure using Azure Developer CLI (AZD). This sample uses manaaged identity and a virtual network to insure it is secure by default. 

## Getting Started

### Prerequisites

1) [Node.js 20](https://www.nodejs.org/) 
2) [Azure Functions Core Tools](https://learn.microsoft.com/azure/azure-functions/functions-run-local?tabs=v4%2Cmacos%2Ccsharp%2Cportal%2Cbash#install-the-azure-functions-core-tools)
3) [Azure Developer CLI (AZD)](https://learn.microsoft.com/azure/developer/azure-developer-cli/install-azd)
4) [Visual Studio Code](https://code.visualstudio.com/) - Only required if using VS Code to run locally

## Run on your local environment

### Prepare your local environment
1) Add a file named local.settings.json file to the root of the project with the following contents. This will allow you to run your function locally.
```json
{
  "IsEncrypted": false,
  "Values": {
    "AzureWebJobsStorage": "UseDevelopmentStorage=true",
    "FUNCTIONS_WORKER_RUNTIME": "node",
    "AzureWebJobsFeatureFlags": "EnableWorkerIndexing"
  }
}
```

### Using Functions CLI
1) Open this folder in a new terminal and run the following commands:

```bash
npm install
func start
```

2) Test the HTTP GET trigger using the browser to open http://localhost:7071/api/httpGetFunction

3) Test the HTTP POST trigger by opening a new command prompt (NOT PowerShell) and navigate to the src/functions folder of the project and run:

```bash
curl -i -X POST http://localhost:7071/api/httppostbodyfunction -H "Content-Type: text/json" --data-binary "@testdata.json"
```

### Using Visual Studio Code
1) Open this folder in a new terminal
2) Open VS Code by entering `code .` in the terminal
3) Press Run/Debug (F5) to run in the debugger (select "Debug anyway" if prompted about local emulater not running) 
4) Insure your favorite REST clientextension is installed (e.g. [RestClient in VS Code](https://marketplace.visualstudio.com/items?itemName=humao.rest-client), PostMan, etc.)
5) Open the file src/functions/test/ which contains a GET and POST test
6) Click the "Send Request" link for each and see the results in the right-hand pane that opens

## Deploy to Azure

To provision the dependent resources and deploy the Function app run the following command:
```bash
azd up
```
You will be prompted for an environment name (this is a friendly name for storing AZD parameters), a Azure subscription, and an Aure location.