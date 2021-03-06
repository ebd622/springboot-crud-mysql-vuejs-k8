# Kubernetes + springboot-crud-mysql-vuejs
This is a Kubernetes design example of the known [springboot-crud-mysql-vuejs](https://github.com/hellokoding/hellokoding-courses/tree/master/springboot-examples/springboot-crud-mysql-vuejs) application from [hellokoding](https://github.com/hellokoding).

It shows how the application can be deployed to a Kubernetes cluster. 

The architecturl design is shown below:

![GitHub Logo](/img/k8_crud_diagram.svg)

**Prerequisites**: An [ingress controller](https://kubernetes.io/docs/concepts/services-networking/ingress-controllers) must be deployed in a cluster, otherwise an Ingress resource has no effect. For example, [Nginx ingress controller](https://docs.nginx.com/nginx-ingress-controller/installation/) can be deployed, follow the [installation](https://docs.nginx.com/nginx-ingress-controller/installation/installation-with-manifests/) instructions to deploy it.

## Deploy the application
The fastest way to deploy the application is to run kubestl **create** command in the src folder:

```
git clone https://github.com/ebd622/springboot-crud-mysql-vuejs-k8.git
cd springboot-crud-mysql-vuejs-k8/src
kubectl create -f .
```

This will deploy all requered kubernetes componenets to your cluster. Wait for a few minutes while the applications is being deployed and open the URL in your browser:
```
http(s)://your_k8_cluster/
```

## Step-by-step deployment
For better understanfing let's deploy the application step-by-step.

**1. Deploy Ingress resources**
```
kubectl create -f ingress-ui-api.yaml
```
This will create ingress rules for the application.


**2. Deploy Secret**
```
kubectl create -f secret.yaml
```
The created secret contains key/value pairs to acceess MySQL DB. The value are mapped to env-variables in the MySQL-container anf crud-api container. Three pairs are configured there:
``` javascript
  dbname: dGVzdA==
  host: aGstbXlzcWw=
  password: aGVsbG9rb2Rpbmc=
```
Secet values must be specified in a hashed format. To decode hash run the command:

```
echo –n ‘dGVzdA==’ | base64 --decode
```
To convert into hash:
```
echo –n ‘my_password’ | base64
```
It is also possible to create a secret in imperative way:
```
kubectl create secret generic mysql-conf --from-literal=password=hellokoding --from-literal=host=hk-mysql --from-literal=dbname=test
```



**3. Deploy ConfigMap**
```
kubectl create -f mysql-cm.yaml
```

**4. Deploy MySQL**
```
kubectl create -f mysql-deploy.yaml
```

**5. Deploy a service for MySQL**
```
kubectl create -f svc-mysql.yaml
```

**6. Deploy crud-api**
```
kubectl create -f crud-api-deploy.yaml
```

**7. Deploy a service for crud-api**
```
kubectl create -f svc-crud-api.yaml
```
This will create a deployment with the image [crud-api-k8](https://github.com/ebd622/crud-api-k8).


**8. Deploy ui-vuejs**
```
kubectl create -f ui-vuejs-deploy.yaml
```
This will create a deployment with the image [ui-vuejs-k8](https://github.com/ebd622/ui-vuejs-k8).


**9. Deploy a service for ui-vuejs**
```
kubectl create -f svc-ui-vuejs.yaml
```

## Deploy with Helm
It is also possible to deploy the application with Helm, a Chart and instructuons are specified in [springboot-crud-mysql-vuejs-helm](https://github.com/ebd622/springboot-crud-mysql-vuejs-helm)

