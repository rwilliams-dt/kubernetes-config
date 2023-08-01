# Prometheus Exporters and MongoDB

1.	Login to GCP:
   
2.	Deploy GKE using GCloud:

    gcloud config set compute/zone us-central1-c

    gcloud container clusters create mongodb-class-robert-williams --machine-type e2-standard-2 --enable-autoscaling --min-nodes 3 --max-nodes 6

3.	Connect to the cluster:
  
4. 	Integrate Dynatrace with GKE and Execute the following commands in your terminal:
    
     kubectl create namespace dynatrace
   	
   	 kubectl apply -f https://github.com/Dynatrace/dynatrace-operator/releases/download/v0.12.1/kubernetes.yaml
   	
     kubectl -n dynatrace wait pod --for=condition=ready --selector=app.kubernetes.io/name=dynatrace-operator,app.kubernetes.io/component=webhook --timeout=300s

   	 kubectl apply -f dynakube.yaml
   	
5.	Deploy MongoDB:

  	 kubectl apply -f mongodb.yaml

6.  Deploy MongoDB Exporter:

     kubectl apply -f mongodb-exporter.yaml
    
7.	Capture IP for MongoDB Service:

     kubectl get all -o wide
  	
8.	Verify MongoDB metrics:

  	 kubectl run mycurlpod --image=curlimages/curl -i -t – sh
  	
     curl http://<mongodb-exporter.ip>:9216/metrics | grep mongo
  	
9.	Enable Kubernetes features in Dynatrace UI:

     Monitor namespaces, services, workspaces, and pods
  	
  	 Monitor persistent volume claims
  	
  	 Monitor annotated Prometheus exporters
  	
  	 Monitor workload and node resource metrics
  	
  	 Monitor events
  	 

11.	Check Metrics in Dynatrace


