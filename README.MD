# ARQUITECTURA DE SOFTWARE 2 - CLASE 2

Labs de la clase

- Namespaces
- Pods
- Pods/Recursos
- Deployment
- Services

## Comandos

Secuencia de comandos para la demo

```bash
# VER YAML DE CREACION DEL NAMESPACE clase2
kubectl create ns clase2 --dry-run=client -o yaml

#CREAR NAMESPACE DESDE YAML
kubectl apply -f namespace.yaml

# CREAR POD EN EL NAMESPACE
kubectl apply -f pod.yaml -n clase2

# VER ESTADO DE POD
kubectl get pods -n clase2

# LIMPIEZA
kubectl delete ns clase2

###############################
# RECURSOS
###############################

#CREAR NAMESPACE DESDE YAML
kubectl apply -f namespace.yaml

kubectl apply -f .\resources\memory-request-limit.yaml -n clase2
kubectl get pods -n clase2
kubectl top pod memory-demo -n clase2
kubectl delete pod memory-demo -n clase2

kubectl apply -f .\resources\memory-request-limit-2.yaml -n clase2
kubectl get pods -n clase2
kubectl delete pod memory-demo-2 -n clase2

kubectl apply -f .\resources\memory-request-limit-3.yaml -n clase2
kubectl get pods -n clase2
kubectl delete pod memory-demo-3 -n clase2

kubectl apply -f .\resources\cpu-request-limit.yaml -n clase2
kubectl get pods -n clase2
kubectl top pod cpu-demo -n clase2
kubectl delete pod cpu-demo -n clase2

kubectl apply -f .\resources\cpu-request-limit-2.yaml -n clase2
kubectl get pods -n clase2
kubectl delete pod cpu-demo-2 -n clase2
# LIMPIEZA

kubectl delete ns clase2
###############################
# DEPLOYMENT
###############################

#CREAR NAMESPACE DESDE YAML
kubectl apply -f namespace.yaml

kubectl apply -f .\deployment.yaml -n clase2

kubectl delete ns clase2

###############################
# SERVICES
###############################
#CREAR NAMESPACE DESDE YAML
kubectl apply -f namespace.yaml
kubectl apply -f .\service.yaml -n clase2

# ejecuta un busybox en forma interactiva
kubectl run -i --tty busybox --image=busybox --restart=Never -n clase2 -- sh

wget  -S -qO- http://service-example.clase2.svc.cluster.local && echo ""
exit
kubectl delete pod busybox
kubectl delete pod busybox -n clase2
```
