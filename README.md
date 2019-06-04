
Make:

	$ mvn package
	
Deploy:

	$ kubectl apply -f istio/deployment.yaml
	$ kubectl apply -f istio/gateway.yaml
	
Determine ingress host & port (load balancer):

	$ export INGRESS_HOST=$(kubectl -n istio-system get service istio-ingressgateway -o jsonpath='{.status.loadBalancer.ingress[0].ip}')
	$ export INGRESS_PORT=$(kubectl -n istio-system get service istio-ingressgateway -o jsonpath='{.spec.ports[?(@.name=="http2")].port}')
	$ export SECURE_INGRESS_PORT=$(kubectl -n istio-system get service istio-ingressgateway -o jsonpath='{.spec.ports[?(@.name=="https")].port}')
	
	
List Pods:

	$ kubectl get pods
	
List Gateways:

	$ kubectl get gateway --all-namespaces
	
