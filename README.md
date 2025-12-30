# Scaleway Serverless Container Deploy

Scaleway has a Serverless service. This GitHub Action uses the Scaleway API to deploy your images in the Scaleway Container Registry into a Serverless Container.

## Usage

In your workflow, use this Action as shown below, filling in the arguments with your own values.

```yaml
  - name: Update container with new image version
    uses: yamatt/scaleway-serverless-container-deploy-action@v1.1
    with:
      container_id: 762bd6f8-1551-4a9c-bd34-5fa11889677a
      secret_key: ${{ secrets.SCALEWAY_SECRET_KEY }}
      registry_image_url: rg.fr-par.scw.cloud/example-registry/example-image:latest
```

> **Note**
> If your code builds images, you will need to use a different Action to put that image into the Scaleway Container Registry.

## Arguments

| Argument             | Description                                                                                                                                                                                                                                  | Required | Default  |
|----------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|:--------:|:--------:|
| `region`             | Scaleway region ID. Currently only `fr-par` supports Serverless but could also be `nl-ams` or `pl-waw` in future.                                                                                                                            |    No    | fr-par   |
| `container_id`       | The UUID of the container. This Action does not create containers, only updates existing ones. You therefore need a container to be created initially, and take the ID from that. The ID can be found in the URL, or the API.                 |   Yes    |   N/A    |
| `secret_key`         | The secret API key used to access Scaleway. This is generated from the Credentials page. This key must be for the right Organization. The key must have access to the Container Registry and the Serverless APIs. Note that Access Key is not used. |   Yes    |   N/A    |
| `registry_image_url` | The URL for the registry, image, and version to use in the container. i.e.: rg.fr-par.scw.cloud/example-registry/example-image:latest                                                                                                        |   Yes    |   N/A    |
| `api_version`        | The version of the API to compare against                                                                                                                                                                                                   |    No    | v1beta1  |

## License

MIT
