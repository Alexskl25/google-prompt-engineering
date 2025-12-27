# google-prompt-engineering
used links:

[`https://github.com/GoogleCloudPlatform/kubectl-ai`](https://github.com/GoogleCloudPlatform/kubectl-ai)

[`https://www.kaggle.com/whitepaper-prompt-engineering`](https://www.kaggle.com/whitepaper-prompt-engineering)

---

## Task
**Please note that for this, all we require is a GitHub repository containing your YAML Kubernetes manifests with prompt. You do not need to provide a Docker image or deploy the application to a Kubernetes cluster. We will review your YAML manifests and provide feedback accordingly.**

---

| NAME | PROMPT | DESCRIPTION | EXAMPLE |
| ------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------- | -------------------------------------------------------------- |
| `app.yaml`                | Create a deployment named go-demo-app. It should have 3 replicas and use the image denvasyliev/go-demo-app:v1.0.0. The container within the deployment should be named go-demo-app and expose port 8080. Also, create a service named go-demo-app-svc of type ClusterIP. This service should expose port 80 and target port 8080 of the go-demo-app deployment. | Base Kubernetes Deployment and ClusterIP Service for a Go application | [`yaml/app.yaml`](yaml/app.yaml) |
| `app-livenessProbe.yaml`  | I have a deployment named go-demo-app. I need to add a liveness probe to the go-demo-app container. The probe should be an HTTP GET request to the /healthz endpoint on port 8080. It should have an initialDelaySeconds of 5 and a periodSeconds of 10. | Adds an HTTP liveness probe to detect unhealthy containers | [`yaml/app-livenessProbe.yaml`](yaml/app-livenessProbe.yaml) |
| `app-readinessProbe.yaml` | I have a deployment named go-demo-app. I want to add a readiness probe to the go-demo-app container. The probe should be an HTTP GET request to the /ready endpoint on port 8080. It should have an initialDelaySeconds of 5 and a periodSeconds of 10. | Adds a readiness probe to control traffic flow to pods | [`yaml/app-readinessProbe.yaml`](yaml/app-readinessProbe.yaml) |
| `app-volumeMounts.yaml`   | I have a deployment named go-demo-app. I want to add a volume to it. The volume should be an emptyDir volume named data. This volume should be mounted in the go-demo-app container at the path /app/data. | Demonstrates using an emptyDir volume and mounting it into a container     | [`yaml/app-volumeMounts.yaml`](yaml/app-volumeMounts.yaml) |
| `app-cronjob.yaml`        | Create a CronJob named go-demo-app-cronjob that runs every minute (* * * * *). The job created by the CronJob should have a container named go-demo-app-cronjob that uses the image busybox and runs the command echo "Hello from the cron job". | Example of a Kubernetes CronJob running on a schedule | [`yaml/app-cronjob.yaml`](yaml/app-cronjob.yaml) |
| `app-job.yaml`            | Create a Job named go-demo-app-job. The Job should have a container named go-demo-app-job that uses the image busybox and runs the command echo "Hello from the job". | One-time Kubernetes Job execution example                                  | [`yaml/app-job.yaml`](yaml/app-job.yaml) |
| `app-multicontainer.yaml` | Create a deployment named go-demo-app-multicontainer. It should have two containers. The first container should be named go-demo-app and use the image denvasyliev/go-demo-app:v1.0.0. The second container should be a sidecar named sidecar, using the image busybox and running the command while true; do echo 'hello from sidecar' >> /var/log/sidecar.log; sleep 5; done. | Multi-container Pod pattern with a sidecar container | [`yaml/app-multicontainer.yaml`](yaml/app-multicontainer.yaml) |
| `app-resources.yaml`      | I have a deployment named go-demo-app. I want to set resource requests and limits for the go-demo-app container. The requests should be 100m for CPU and 128Mi for memory. The limits should be 200m for CPU and 256Mi for memory. | Sets CPU and memory requests and limits for containers | [`yaml/app-resources.yaml`](yaml/app-resources.yaml) |
| `app-secret-env.yaml`     | First, create a secret named go-demo-app-secret with a key MY_SECRET and the value mysecretvalue. Then, create a deployment named go-demo-app that uses the image denvasyliev/go-demo-app:v1.0.0. The go-demo-app container should have an environment variable named MY_SECRET_ENV that gets its value from the MY_SECRET key in the go-demo-app-secret secret. | Uses Kubernetes Secrets to inject sensitive data via environment variables | [`yaml/app-secret-env.yaml`](yaml/app-secret-env.yaml) |
