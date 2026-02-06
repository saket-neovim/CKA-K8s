# Kubernetes Manifests

This folder contains a collection of learning and lab manifests grouped by day/task. Files are organized as they were created during exercises.

## Quick Use

Apply a single manifest:
```bash
kubectl apply -f k8s/day12/deployment.yaml
```

Apply a whole folder:
```bash
kubectl apply -f k8s/day13/
```

Delete resources from a file:
```bash
kubectl delete -f k8s/day12/deployment.yaml
```

## Safety Notes

- Do not commit real credentials, private keys, or certificates. Use placeholders like `<REDACTED_PASSWORD>`.
- Files under `day20/` that contain CSR/CRT/KEY content are redacted for public sharing.
- If you use `Secret` objects with `data:` or `stringData:`, keep them out of public repos.

## Suggested Improvements (Optional)

- Add namespaces to isolate exercises (e.g., `metadata.namespace: lab`).
- Convert related files into `kustomization.yaml` bundles for easier application.
- Replace inline values with `ConfigMap` and `Secret` objects when scaling up.

## Repo Hygiene

This repo includes a nested `k8s/.git` directory from earlier experiments. If you plan to publish the repo, remove it:
```bash
rm -rf k8s/.git
```
