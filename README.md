# Scaleway Serverless Container Deploy

Scaleway have a Serverless service. This GitHub Action uses the Scaleway API to deploy your images in the Scaleway Container Registry in to a Serverless Container.

## Usage

In your workflow use this Action like so, filling in the arguments with your own values.

```yml
      - name: update container with new image version
        uses: yamatt/scaleway-serverless-container-deploy-action@v1.1
        with:
          container_id: 762bd6f8-1551-4a9c-bd34-5fa11889677a
          secret_key: ${{ secrets.SCALEWAY_SECRET_KEY }}
          registry_image_url: rg.fr-par.scw.cloud/example-registry/example-image:latest
```

Note if your code builds images, you will need to use a different Action to put that image in to the Scaleway Container Registry

## Arguements

| Argument             | Description                                                                                                                                                                                                                                  | Required | Default |
|----------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|----------|---------|
| `region`             | Scaleway region ID. Currently only `fr-par` supports Serverless but could also be `nl-ams` or `pl-waw` in future.                                                                                                                            | ❌        | fr-par  |
| `container_id`       | The UUID of the container. This Action does not create containers, only update existing ones. You therefore need a container to be created initially, and take the ID from that. The ID can be found in the URL, or the API.                 | ✔️        | N/A     |
| `secret_key`         | The secret API key used to access Scaleway. This is generated from the Credentials page. This key must be for the right Organization. The key must have access to the Container Registry and the Serverless APIs. Note that Access Key is not used. | ✔️        | N/A     |
| `registry_image_url` | The URL for the registry, image, and version to use in the container. i.e.: rg.fr-par.scw.cloud/example-registry/example-image:latest                                                                                                        | ✔️        | N/A     |
| `api_version` | The version of the API to compare against | ❌        | v1beta1     |

## License

MIT
