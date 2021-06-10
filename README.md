# Basic Auth Service

Protects all our staging sites.

```sh
kubectl kustomize
kubectl apply -k .
```

```sh
kubectl exec -ti <some-pod-in-cluster> -- bash
curl -k basic-auth-service.default.svc.cluster.local -v -u 'username:password'
```

## Resources

- [Authenticate requests to apps on kubernetes using Nginx-Ingress and an AuthService.](https://medium.com/@ankit.wal/authenticate-requests-to-apps-on-kubernetes-using-nginx-ingress-and-an-authservice-37bf189670ee)
- [External Basic Authentication](https://kubernetes.github.io/ingress-nginx/examples/auth/external-auth/)

