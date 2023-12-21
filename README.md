# ISSA Web Application Backend Services

The [ISSA project](https://issa.cirad.fr/) focuses on the semantic indexing of scientific publications in an open archive.

This repository is the backend part of a web application that demonstrates the interest and use of such a semantic index for researchers and librarians.
It provides a set of Web APIs (services) used by the frontend application  available in the [visualization repository](https://github.com/issa-project/visualization).


### Services

The services exposed by the server are defined in [routes/index.js](routes/index.js).

With the exception of service `autoComplete`, the services submit SPARQL SELECT [queries](queries) to the ISSA SPARQL endpoint (property SEMANTIC_INDEX_SPARQL_ENDPOINT in [.env](.env))
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
http://localhost:3000/getArticleMetadata?uri=http://data-issa.cirad.fr/document/592919
```
(this is an example article URI that may no longer be valid at some point).


### Logging

Log traces are printed out in file `log/application.log`.

This can be changed by customizing file [config/log4js.json](config/log4js.json).
Refer to the [Log4JS documentation](https://stritti.github.io/log4js/).



## License

See the [LICENSE file](LICENSE).


## Cite this work

Franck MICHEL, Youssef MEKOUAR, ISSA Project (2023). ISSA Web Application Backend Services. https://github.com/issa-project/web-backend/.


## Publications

ISSA: Generic Pipeline, Knowledge Model and Visualization tools to Help Scientists Search and Make Sense of a Scientific Archive.
Anne Toulet, Franck Michel, Anna Bobasheva, Aline Menin, Sébastien Dupré, Marie-Claude Deboin, Marco Winckler, Andon Tchechmedjiev.
_21st International Semantic Web Conference (ISWC)_, Oct 2022, Hangzhou, China. DOI: [⟨10.1007/978-3-031-19433-7_38⟩](https://dx.doi.org/10.1007/978-3-031-19433-7_38). [HAL](https://hal.science/hal-03807744)
