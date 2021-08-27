# Basic Auth Service

Protects all our staging sites.

Download `.htpasswd` attachment from [Bitwarden](https://bitwarden.veri.ie) > Collections > Developers > auth-staging.veri.ie

```sh
kubectl kustomize
kubectl apply -k .
kubectl rollout restart deployment basic-auth
```

Add more usernames and passwords.

```sh
htpasswd .htpasswd <username>
```

Update ingress of your application with

```yaml
annotations:
    nginx.ingress.kubernetes.io/auth-url: https://basic-auth.veri.ie/
```

```sh
kubectl exec -ti <some-pod-in-cluster> -- bash
curl -k basic-auth-service.default.svc.cluster.local -v -u 'username:password'
```

## Resources

- [Authenticate requests to apps on kubernetes using Nginx-Ingress and an AuthService.](https://medium.com/@ankit.wal/authenticate-requests-to-apps-on-kubernetes-using-nginx-ingress-and-an-authservice-37bf189670ee)
- [External Basic Authentication](https://kubernetes.github.io/ingress-nginx/examples/auth/external-auth/)

