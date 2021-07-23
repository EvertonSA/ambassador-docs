import Alert from '@material-ui/lab/Alert';

# Quick start

## OpenAPI

You can visualize and explore your service’s OpenAPI specification (formerly known as Swagger) documentation from within Ambassador Cloud.

## Prerequisites

1. You must have [Ambassador Edge Stack version 2.0+ installed and connected to Ambassador Cloud](../../service-catalog/quick-start) in your
   Kubernetes cluster. This guide assumes you have deployed the `quote` application and resources from the Service Catalog quick start.
2. Enable reporting the `quote` service documentation by creating, or editing, the `quote-backend` AmbassadorMapping resource with the following docs path `/.ambassador-internal/openapi-docs`

   ```
   echo '---
   apiVersion: x.getambassador.io/v3alpha1
   kind: AmbassadorMapping
   metadata:
     name: quote-backend
     namespace: ambassador
   spec:
     hostname: "*"
     prefix: /backend/
     service: quote
     docs:
       path: '/.ambassador-internal/openapi-docs'
   ' | kubectl apply -f -
   ```

## Visualize the API Documentation

1. Navigate to [Ambassador Cloud](https://app.getambassador.io/cloud/services) to see your connected services.

2. Select the quote service from the Service Catalog page.

3. Click on the API tab to access the rendered OpenAPI documentation.

## <img class="os-logo" src="../../images/logo.png"/> What's next?

You've published your service documentation on Ambassador Cloud to enable collaboration with other teams and members of your organization, but you can extend your services AmbassadorMapping with [other Developer Portal docs options](../../../edge-stack/latest/topics/using/dev-portal/#docs-attribute-in-mappings), and **Service Catalog annotations!**  See the full list of service annotations [here](../reference/annotations/).
