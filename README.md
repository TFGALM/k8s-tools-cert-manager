# cert-manager

Este servicio nos sirve para muchas cosas, su principal funcion es generar y rotar certificados, pero no nos dejan tener una CA en kubernetes ni que kubernetes use la CA. Así que su uso se limita en gestionar los certificados.

## Despliegue servicio

``` shell
helm repo add jetstack https://charts.jetstack.io
helm repo update
# helm show values jetstack/cert-manager --version v1.16.1 > values.default.yaml
# helm show values jetstack/trust-manager --version v0.13.0 > values.default.yaml
helm upgrade cert-manager jetstack/cert-manager --install -f manifests/values-1-16-1.yaml -n cert-manager --create-namespace --version v1.16.1
helm upgrade trust-manager jetstack/trust-manager --install -f manifests/values-trust-manager-0-13-0.yaml -n cert-manager --create-namespace --version v0.13.0
kubectl apply -f trust-manifests/
```


