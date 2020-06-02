# Kubernetes + springboot-crud-mysql-vuejs
This is a Kubernetes design example of the known [springboot-crud-mysql-vuejs](https://github.com/hellokoding/hellokoding-courses/tree/master/springboot-examples/springboot-crud-mysql-vuejs) application from [hellokoding](https://github.com/hellokoding).

It shows how the application can be deployed to a Kubernetes cluster. 

The architecturl design is shown below:

![GitHub Logo](/img/k8_crud_diagram.svg)

**Prerequisites**: An [ingress controller](https://kubernetes.io/docs/concepts/services-networking/ingress-controllers) must be deployed in a cluster, otherwise an Ingress resource has no effect. For example, [Nginx ingress controller](https://docs.nginx.com/nginx-ingress-controller/installation/) can be deployed.

## Deploy the application
The fastest way to deploy the application is to run kubestl create command in the src folder:

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

1. Deploy Ingress resources

2. Deploy Secret

3. Deploy ConfigMap

4. Deploy MySQL

5. Deploy a service for MySQL

6. Deploy crud-api

7. Deploy a service for crud-api

8. Deploy ui-vuejs

9. Deploy a service for ui-vuejs

