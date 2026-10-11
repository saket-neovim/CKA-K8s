# Kubernetes Administration Practice Manifests

Kubernetes learning manifests organized by day and task: Pods, Deployments, Services, scheduling, storage, RBAC, network policies, and certificate-signing requests. The collection supports administration practice and CKA study; it does not claim certification or a production cluster deployment.

## Repository guide

| Area | Examples |
| --- | --- |
| Local cluster | [config.yaml](config.yaml), [config-networking.yaml](config-networking.yaml) for kind |
| Workloads and Services | `day07/`–`day14/`, plus root practice manifests |
| Scheduling and metrics | `day15/`, `day17/metrics-server.yaml` |
| Identity and permissions | [day20/learner-csr.yaml](day20/learner-csr.yaml), `day23/`, `day24/` |
| Network policy | [day26/task/network-policy.yaml](day26/task/network-policy.yaml) |
| Storage and sample web content | `day29/` |

## Prerequisites and examples

Use `kubectl` and a disposable cluster. For the kind configuration, install kind and a compatible container runtime.

```bash
kind create cluster --name cka-lab --config config.yaml
kubectl config current-context
kubectl apply --dry-run=client -f day09/deploy.yaml
kubectl apply --dry-run=server -f day09/deploy.yaml
```

Client dry-run checks local handling; server dry-run also requires a cluster and checks API/admission behavior. Review the current context before actual applies and use a dedicated lab cluster. Choose manifests individually; duplicate object names and unrelated exercises make a repository-wide apply inappropriate.

## Validation and limitations

Check workload readiness, Service endpoints, RBAC with `kubectl auth can-i`, and the behavior of the selected networking/storage exercise. NetworkPolicy enforcement depends on the cluster network plugin, and `hostPath` examples depend on node-local paths. Review image versions and API compatibility for your cluster.

The CSR example contains a placeholder request. Generate a new key/request locally and substitute its base64 value before using it. Generated signed CSR exports, issued certificate output, and cluster-specific metadata have been removed from current tracked examples; a saved export is not a reusable manifest.

## Cleanup and security

Delete the disposable kind cluster when finished:

```bash
kind delete cluster --name cka-lab
```

For other clusters, delete only resources from your selected exercise after checking their namespace and ownership; persistent storage needs a separate retention decision. Keep private keys, kubeconfig, tokens, certificate exports, and real host paths out of Git. Older revisions can retain removed artifacts. No runtime completion evidence is claimed by the presence of these manifests.
