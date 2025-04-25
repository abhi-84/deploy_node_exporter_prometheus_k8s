Apply deployment file
# kubectl apply -f node-exporter-deployment.yaml
4.6 Verify node-exporter deployment
# kubectl get pods -l app=node-exporter
Apply node-exporter service
# kubectl apply -f node-exporter-service.yaml
Verify
# kubectl get services -l app=node-exporter

Apply prometheus ConfigMap
# kubectl apply -f prometheus-config.yaml
Apply prometheus deployment
# kubectl apply -f prometheus-deploy.yaml
Check if pod successfully starts
# kubectl get pods -l app=prometheus
Apply Prometheus Service
# kubectl apply -f prometheus-service.yaml
Verify Prometheus service running.
# kubectl get svc prometheus-service

if bith packages are runing correctly, one should able to see "UP" status in prometheus dashboard as shown.

![image](https://github.com/user-attachments/assets/2f5745ce-2a45-4649-a89a-acf49cd65fe8)

Now we can use host IP:30090 to Grafana dashboard and display metrics on dashboard

