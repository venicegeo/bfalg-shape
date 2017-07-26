# bfalg-shape

### Building:

### Writing your pzsvc-exec.config file:
* CliCmd is executed within a subfolder within pzsvc-exec, so the path to your algorithm should be proceeded by ` ../ `
* VersionCmd is not executed within a subfolder within pzsvc-exec, so the path to your algorithm stays as it looks in your app

### Registering with pzsvc-exec:
* Your algorithm repo should be located inside the pzsvc-exec directory
* pzsvc-exec.config should also be located inside the pzsvc-exec directory
```
export PZ_ADDR=https://piazza.int.geointservices.io
export PZ_API_KEY=******
go build
./pzsvc-exec pzsvc-exec.config
```

### Running a piazza job with your algorithm:
* An example job creation cURL command for bfalg-shape would look like:
```
POST to https://piazza.int.geointservices.io/job
-Include API key in header
{
  "data": {
    "dataInputs": {
      "body": {
        "content": "{\"cmd\":\"-u \\\"https://landsat-pds.s3.amazonaws.com/L8/139/045/LC81390452014295LGN00/LC81390452014295LGN00_B1.TIF\\\" \"}",
        "type": "body",
        "mimeType": "application/json"
      }
    },
    "dataOutput": [{"mimeType": "application/json","type": "text"}],
    "serviceId": "238e8795-1a4d-4220-8f5c-e6434f2c4373"
  },
  "type": "execute-service"
}
```
* Notice URLs must be surrounded by double-quotations, which must be double-escaped with ` \\\ `
