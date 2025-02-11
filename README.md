# Excalidraw Helm Chart

This repository contains a Helm chart for deploying the [Excalidraw](https://github.com/excalidraw/excalidraw) container using Kubernetes. The chart facilitates the deployment of Excalidraw using the official Docker image from [Docker Hub](https://hub.docker.com/r/excalidraw/excalidraw).

## Features
- Deploys Excalidraw as a Kubernetes service
- Configurable via `values.yaml`
- Uses a `renovate.json` configuration for automatic image updates with [Mend Renovate](https://www.mend.io/)
- Targets SHA digest for updates due to the container not following semantic versioning (SemVer)

## Installation

### Prerequisites
- Kubernetes cluster
- Helm installed ([Installation Guide](https://helm.sh/docs/intro/install/))

### Deploying Excalidraw
1. Add the Helm repository (if applicable) or clone this repository:
   ```sh
   git clone https://github.com/jimmylin/excalidraw.git
   cd excalidraw
   ```
2. Install the Helm chart:
   ```sh
   helm install excalidraw ./chart
   ```
3. Check the deployed resources:
   ```sh
   kubectl get pods,svc
   ```

## Configuration
Customize the deployment using `values.yaml`. Key parameters include:

| Parameter         | Description                          | Default Value |
|------------------|----------------------------------|---------------|
| `replicaCount`   | Number of replicas               | `1`           |
| `image.repository` | Container image repository     | `excalidraw/excalidraw` |
| `image.pullPolicy` | Image pull policy             | `Always`      |
| `service.type`    | Kubernetes service type        | `ClusterIP`   |
| `service.port`    | Service port                   | `80`          |

To customize, edit `values.yaml` or use `--set` flags:
```sh
helm install excalidraw ./chart --set replicaCount=2
```

## Automatic Updates with Renovate
This repository includes a `renovate.json` file to automate image updates using [Mend Renovate](https://www.mend.io/). Since the Excalidraw container does not follow semantic versioning, Renovate is configured to track the latest SHA digest instead of tags.

To enable Renovate:
1. Ensure you have Renovate set up for your repository.
2. Check `.github/renovate.json` for update configurations.
3. Renovate will automatically create PRs when a new image SHA is available.

## Uninstalling
To remove the deployment:
```sh
helm uninstall excalidraw
```

## License
This project is licensed under the [MIT License](LICENSE).

## Contributing
Contributions are welcome! Please open an issue or submit a pull request.

## Contact
For questions, reach out via GitHub Issues.

