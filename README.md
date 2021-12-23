# kubernetes-useful-templates

This project provides useful golang templates and go templates examples that customize the output of kubectl get resources

## Usage example

### Example Use the template file

```shell
kubectl get pods -ogo-template-file=./get-pods-requested-resources.tmpl
kubectl get pods -ogo-template-file=./get-pods-requested-resources.tmpl --all-namespaces

```

### Use the content of the template

Get single value from a secret:

```shell

kubectl get secrets my-secret --template='{{.data.password | base64decode}}'
```

Get all key values from a secret:

```shell
kubectl get secrets my-secret --template='{{ range $key, $value := .data }}{{ printf "%s: %s\n" $key ($value | base64decode) }}{{ end }}'
```

Description: this go template will output csv output with the requested resources of all containers inside a pod

## Template file

| Template file | Description | 
|----------|:-------------:|
| get-all-secrets-decoded.tmpl |  Output all secret objects as key: value and decode the output |
| get-pods-requested-resources.tmpl | Output csv output with the requested resources of all containers inside a pod |
