# Alfresco Content Services (ACS) Helm Chart

This chart deploys Postrges, ActiveMQ and the Alfresco repository.

## Deploy

```bash
cd helm
helm dependency update alfresco-content-services
helm install acs alfresco-content-services -n devops-test
```

The repository service is available via `NodePort`.
