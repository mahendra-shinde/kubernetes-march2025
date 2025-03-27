# Introduction to GitOps
GitOps is a modern approach to continuous deployment that uses Git as the single source of truth for declarative infrastructure and application configurations. By leveraging Git, teams can manage and track changes to their systems in a version-controlled and auditable manner.

ArgoCD is a popular GitOps tool designed for Kubernetes. It continuously monitors Git repositories for changes and ensures that the desired state defined in Git matches the actual state of the Kubernetes cluster. ArgoCD provides features like automated synchronization, rollback capabilities, and a user-friendly web interface for managing deployments.

## Steps to Install Argo CD in Kubernetes cluster
1. **Install Argo CD Namespace**  
    Create a namespace for Argo CD in your Kubernetes cluster:  
    ```bash
    kubectl create namespace argocd
    ```

2. **Install Argo CD**  
    Apply the Argo CD installation manifests:  
    ```bash
    kubectl apply -n argocd -f https://raw.githubusercontent.com/argoproj/argo-cd/stable/manifests/install.yaml
    ```

3. **Access the Argo CD Server**  
    By default, the Argo CD server is exposed as a ClusterIP service. To access it, you can port-forward the service:  
    ```bash
    kubectl port-forward svc/argocd-server -n argocd 8080:443
    ```

4. **Retrieve the Admin Password**  
    The initial admin password is stored in a Kubernetes secret. Retrieve it using the following command:  
    ```bash
    kubectl get secret argocd-initial-admin-secret -n argocd -o jsonpath="{.data.password}" 
    ```

5. Decode the BASE64 encoded password from last command using powershell

    ```powershell
    [System.Text.Encoding]::UTF8.GetString([System.Convert]::FromBase64String("<BASE64_PASSWORD>"))

    ```
    Replace `<BASE64_PASSWORD>` with the output from the previous command.
    

5. **Login to Argo CD**  
    Open your browser and navigate to `https://localhost:8080`. Use the username `admin` and the password retrieved in the previous step to log in.

