Here, I presume that K8S is already running in your host system. 
Prometheus and Node-Exporter are hosted on Kubernetes, and Prometheus is linked to Grafana (not running on Kubernetes, but locally) to display metric values.

Install Prometheus, node-exporter and Grafana
Apply the deployment file
# kubectl apply -f node-exporter-deployment.yaml
Verify node-exporter deployment
# kubectl get pods -l app=node-exporter
Apply the node-exporter service
# kubectl apply -f node-exporter-service.yaml
Verify
# kubectl get services -l app=node-exporter

Apply Prometheus ConfigMap
# kubectl apply -f prometheus-config.yaml
Apply Prometheus deployment
# kubectl apply -f prometheus-deploy.yaml
Check if pod successfully starts
# kubectl get pods -l app=prometheus
Apply Prometheus Service
# kubectl apply -f prometheus-service.yaml
Verify the Prometheus service is running.
# kubectl get svc prometheus-service

If both packages are running correctly, one should be able to see "UP" status in Prometheus dashboard as shown.

![image](https://github.com/user-attachments/assets/2f5745ce-2a45-4649-a89a-acf49cd65fe8)

Set up Grafana
$ sudo apt-get install -y adduser libfontconfig1 musl 
$ wget https://dl.grafana.com/enterprise/release/grafana-enterprise_11.6.0_amd64.deb 
$ sudo dpkg -i grafana-enterprise_11.6.0_amd64.deb
$ systemctl start grafana-server.service
$ sudo systemctl daemon-reload
$ sudo systemctl daemon-reload

• Grafana server will start on http://localhost:3000/
• Username: admin
• Password: admin

Open grafana and create new data source. Select Prometheus and use host IP in URL http://IP_address:30090 and save it.

<img width="1046" height="642" alt="image" src="https://github.com/user-attachments/assets/04c598fb-5735-4d87-ae89-8c37bdc395f9" />

Create new dashboard and add data source just created. Select the metric which is required to be displayed in graph.

<img width="1121" height="632" alt="image" src="https://github.com/user-attachments/assets/2d276860-fa26-4c5e-ad97-872b76b449f1" />

After selecting metrics, click “run queries” button. Select the refresh to 5s to see changes quickly.

<img width="1121" height="632" alt="image" src="https://github.com/user-attachments/assets/4bb7569a-95df-48e4-a091-4d819388b341" />


