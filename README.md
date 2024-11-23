# Lw-task-3-set-1

Scenario : Auto-Scaling a Kubernetes Deployment
 Based on CPU Utilisation.


 I'd create the necessary Kubernetes configurations for deploying an Nginx application with Horizontal Pod Autoscaling based on CPU utilization.

Let me explain each component of the configuration:

Deployment Configuration:

Creates an Nginx deployment using the latest image
Sets resource requests and limits as specified
CPU request: 100m (0.1 CPU cores)
CPU limit: 500m (0.5 CPU cores)


Service Configuration:

Creates a ClusterIP service to expose the Nginx deployment
Maps port 80 for HTTP traffic


HorizontalPodAutoscaler Configuration:

Uses the autoscaling/v2 API version for advanced configuration
Targets the nginx-deployment
Sets min replicas to 1 and max replicas to 10
Configures scaling based on 50% CPU utilization



To apply these configurations:
 kubectl apply -f deployment.yaml
 
kubectl apply -f service.yaml

kubectl apply -f hpa.yaml

To monitor the HPA:
bashCopykubectl get hpa nginx-hpa --watch
To test the autoscaling, you can generate load on the pods using a tool like hey or ab (Apache Benchmark). The HPA will:

Scale up when CPU utilization goes above 50%
Scale down when CPU utilization drops below 50%
Maintain between 1 and 10 replicas




