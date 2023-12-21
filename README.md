### Services

The services exposed by the server are defined in [routes/index.js](routes/index.js).

With the exception of service `autoComplete`, the services submit SPARQL SELECT [queries](queries) to the D2kAB SPARQL endpoint (property SEMANTIC_INDEX_SPARQL_ENDPOINT in [.env](.env))
using the d3-sparql library.
The response of the services is the output of the d3-sparql library itself, that only returns the "results.bindings" part
of the SPARQL response in JSON format, following this format:

```json
{
  "result": [
    {
      "var1": "value1",
      "var2": "value2",
      ...
    }, 
    ...
]}
```

Therefore, the SELECT clause of the SPARQL queries are the de facto documentation of the services 
since they give the names of the variables (var1 and var2 in the example above).


## Installation

Pre-requisite: [node.js](https://nodejs.org/) 17, yarn.

Install the dependencies with `yarn install`.


## Run

Run the application: ` yarn start`

By default, the node.js server listens on port 3000. This can be changed in file [.env](.env).

Make sure the server is properly started by pointing your browser to:
```
http://localhost:3000/getArticleMetadata/?uri=https://pubmed.ncbi.nlm.nih.gov/10099937

```
(this is an example article URI that may no longer be valid at some point).


### Logging

Log traces are printed out in file `log/application.log`.

This can be changed by customizing file [config/log4js.json](config/log4js.json).
Refer to the [Log4JS documentation](https://stritti.github.io/log4js/).



