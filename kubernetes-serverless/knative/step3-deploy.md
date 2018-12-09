To deploy an application on Knative the same kubectl CLI tool can be used just like any other Kubernetes based application. The difference is in the YAML declaration using a resource called _service_. This is not to be confused with the core Kubernetes service resource, instead this is a resource for Knative. It's declaration look like this, 

`curl https://raw.githubusercontent.com/knative/docs/master/serving/samples/helloworld-go/service.yaml`{{execute}}

Notice the kind _Service_ and the apiVersion that defines its context. Using this services resource and YAML, deploy an example Hello World application written in Go. The code and app container has already been published to a registry.

`kubectl create -f https://raw.githubusercontent.com/knative/docs/master/serving/samples/helloworld-go/service.yaml`{{execute}}

At this point you might expect some resources such as Pods spinning up as part of this create.

`kubectl get deployments,rs,pods,services`{{execute}}

There is nothing there, and that is what should happen, since there has been no request to the service, there is no need for the service to consume any resources. The service   is there, and it can be seen with this command.

`kubectl get ksvc helloworld-go`{{execute}}

`kubectl get routes`{{execute}}