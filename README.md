# Devops-assignment-step-3
Create SSL Certificates for nginx in Kubernetes , manage the SSL Certificate in Kubernetes with Cert-Manager, use the ssl Certificate in Traefik Ingress Controller. 


# Summary
- 1 install cert-manager on kubernetes cluster (https://cert-manager.io/docs/installation/helm/) :
- $ helm install cert-manager jetstack/cert-manager --namespace cert-manager --set insallCRDs=true

- 2 create secret for the dns provider :
- $ kubectl apply -f .\secret-cloudflare.yml
![image](https://user-images.githubusercontent.com/113102456/233783458-ab8c6371-a082-4fac-baab-57cc875c04a3.png)

- 3 Create and configure cluster issuer:
- $ kubectl apply -f .\clusterissuer-acme.yml
![image](https://user-images.githubusercontent.com/113102456/233783476-0bd56a69-0a0a-4f56-aa37-07734017c0a1.png)

- 3 Create new A record in your dns provider iclude your public ip 

- 4 Create the Cert:
- $ kubectl apply -f .\certificate.yaml
![image](https://user-images.githubusercontent.com/113102456/233780124-1a2e91a3-8192-4904-848a-0e30951a1e7a.png)

- 5 Deploy the nginx:
- $ kubectl apply -f .\deploy
- $ kubectl apply -f .\service
![image](https://user-images.githubusercontent.com/113102456/233780197-3cf1e1ba-b5cf-4e06-af3d-fd7a350f2faf.png)
![image](https://user-images.githubusercontent.com/113102456/233780206-617e436c-3a18-4927-b94f-5e8b65402521.png)

- 6 Deploy ingress that allow the http traffic:
- $ kubectl apply -f .\nginx-ingress.yml
![image](https://user-images.githubusercontent.com/113102456/233780251-7fd3c811-3779-4f3c-b574-f35d6787f6d0.png)

- 7 paste the url: nginx1.omriv.com in your browser:
![image](https://user-images.githubusercontent.com/113102456/233780453-a08b08ac-9194-411f-9fe8-d5a729c020fc.png)

