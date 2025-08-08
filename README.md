# MkDocs Helm Chart

A minimal Helm chart for deploying [MkDocs Material]('https://hub.docker.com/r/squidfunk/mkdocs-material') documentation sites on Kubernetes.

## Quick Start

1. Create your documentation directory with `mkdocs.yml` and `docs/` folder
2. Install the chart:

```bash
helm install my-docs . --set docs.path=$(pwd)/example
```

3. Access your docs:

```bash
kubectl port-forward svc/my-docs-mkdocs-helm-chart 8080:8000
```

Open http://localhost:8080

## Configuration

#### Required

| Parameter   | Description                          | Example                           |
|-------------|--------------------------------------|-----------------------------------|
| `docs.path` | Path to your documentation directory | `/home/user/my-project/docs-root` |

#### Optional

| Parameter               | Default                     | Description            |
|-------------------------|-----------------------------|------------------------|
| `replicaCount`          | `1`                         | Number of pod replicas |
| `image.repository`      | `squidfunk/mkdocs-material` | Docker image           |
| `image.tag`             | Chart appVersion            | Image tag              |
| `service.port`          | `8000`                      | Service port           |
| `ingress.enabled`       | `false`                     | Enable ingress         |
| `ingress.hosts[0].host` | `docs.example.com`          | Hostname               |

## Examples

### Basic Installation

### With Ingress
```bash
helm install my-docs . \
  --set docs.path=/path/to/docs \
  --set ingress.enabled=true \
  --set ingress.hosts[0].host=docs.mycompany.com
```

### Using values.yaml
```yaml
docs:
  path: /path/to/your/documentation

ingress:
  enabled: true
  hosts:
    - host: docs.example.com
      paths:
        - path: /
          pathType: Prefix
```

```bash
helm install my-docs . -f values.yaml
```

### Contributing
Feel free to submit issues and pull requests. I'd appreciate feedback!