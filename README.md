# OpenAPI Workflow

As number of APIs grow, OpenAPI Specifications (OAS) might need to split into multiple files for a easy reading source code.

However, services like AWS API Gateway only support single OAS file import. 

Here are the useful open source tools that is useful for combine or resolve multiple files reference into single file for you OAS.

### Yamlinc - [[Link]](https://github.com/javanile/yamlinc)

Create a composed YAML file using $include tag. Useful for reference multiple files on sibling elements.

```yaml
## file: paths.yml
paths:
  $include: first-paths.yml
  $include: second-paths.yml
  $include: others-paths.yml
```

```yaml
## file: first-paths.yml
/api/first/one:
  get: ...      
/api/first/two:
  post: ...
```

**Usage**
```bash
$ yamlinc --output result.yaml input.yml
```

### Multi-file Swagger [[Link]](https://github.com/mohsen1/multi-file-swagger-example)

Used to resolve remote or URL reference in OAS that using [$ref](https://swagger.io/docs/specification/using-ref/).

```yaml
## file: paths.yml
/foo:
  $ref: ./foo.yaml
/bar:
  $ref: ./bar.yaml
```

```yaml
## file: bar.yml
get:
  responses:
    200:
      description: OK
      schema:
        $ref: '#/definitions/User'
```

> Note that local reference will not resolved.

**Usage**
```bash
$ multi-file-swagger -o yaml source.yaml > compiled.yaml
```
