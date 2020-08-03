# kubernetes-configmaps-secrets

# Pre-Requisites:
    EKS-Cluster
# Encrypt password by using below command
    echo -n "admin123" | base64
# Deploy mysql using below commands
    kubectl apply -f mysql-pvc.yaml
    kubectl apply -f mysql-secrets.yaml
    kubectl apply -f mysql-secrets-deployment.yaml
    kubectl apply -f mysql-service.yaml
# Connect to pod and check weather mysql is working or not   
    kubectl get pods
    kubectl exec -it mysql-deployment-66b46c88f6-gcmjv -- /bin/bash
    mysql -u root -p
Give password as "admin123"
# CleanUp:
    kubectl delete deploy mysql-secrets-deployment
# Deploy mysql using below commands    
    kubectl apply -f mysql-configmaps.yaml
    kubectl apply -f mysql-config-deployment.yaml
# Connect to pod and check weather mysql is working or not    
    kubectl get pods
    kubectl exec -it mysql-config-deployment-578bd76498-ncwll -- /bin/bash
    mysql -u root -p
Give passwoed as "admin123"
# CleanUp:
    kubectl delete deploy mysql-config-deployment
