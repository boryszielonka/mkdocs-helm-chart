# Getting Started

Welcome to the getting started guide for this example documentation!

## Prerequisites

Before you begin, make sure you have:

- Kubernetes cluster running
- Helm 3.x installed
- kubectl configured to access your cluster

## Installation

1. Clone the repository:
   ```bash
   git clone <your-repo-url>
   cd your-docs-project
   ```

2. Install the Helm chart:
   ```bash
   helm install my-docs ./mkdocs-helm-chart --set docs.path=/path/to/your/docs
   ```

3. Access your documentation:
   ```bash
   kubectl port-forward svc/my-docs-mkdocs-helm-chart 8080:8000
   ```

   Then open [http://localhost:8080](http://localhost:8080) in your browser.

## Configuration

### Basic Configuration

The simplest configuration requires only setting the `docs.path` value:

```yaml
docs:
  path: /path/to/your/documentation
```

### Ingress Configuration

To expose your documentation with ingress:

```yaml
ingress:
  enabled: true
  hosts:
    - host: docs.yourcompany.com
      paths:
        - path: /
          pathType: Prefix
```
