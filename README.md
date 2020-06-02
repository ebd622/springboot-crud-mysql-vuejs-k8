# Kubernetes + springboot-crud-mysql-vuejs
This is a Kubernetes design example of the known [springboot-crud-mysql-vuejs](https://github.com/hellokoding/hellokoding-courses/tree/master/springboot-examples/springboot-crud-mysql-vuejs) application from [hellokoding](https://github.com/hellokoding).

It shows how the application can be deployed to a Kubernetes cluster. 

The architecturl design is shown below:

![GitHub Logo](/img/k8_crud_diagram.svg)

Prerequisites: An [ingress controller](https://kubernetes.io/docs/concepts/services-networking/ingress-controllers) must be deployed in a cluster, otherwise an Ingress resource has no effect. For example, [Nginx ingress controller](https://docs.nginx.com/nginx-ingress-controller/installation/) can be installed.


