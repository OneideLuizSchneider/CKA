#### SECURITY

- TLS
  - Look at the apiserver cert:
    - `openssl x509 -in /etc/kubernetes/pki/apiserver.crt -text -noout`
  - More: <https://kubernetes.io/docs/tasks/administer-cluster/certificates/>


- Auth with a `CertificateSigningRequest`:
  - To generate a cert:
    - ```
        openssl genrsa -out myuser.key 2048
        
        openssl req -new -key myuser.key -out myuser.csr -subj "/CN=myuser"

        cat myuser.csr | base64 | tr -d "\n"
      ```
  - To apply it:
    - `kubectl apply -f /help/CertificateSigningRequest.yml`
    - To see it: `kubectl get csr`
    - To approve it: `kubectl certificate approve myuser`
    - To deny it:  `kubectl certificate deny myuser`
  - Doc: <https://kubernetes.io/docs/reference/access-authn-authz/certificate-signing-requests/>

- Kubeconfig
  - Default path:
    - `/root/.kube/`
  - List all clusters:
    - `k config get-clusters`
  - List all users:
    - `k config get-users`
  - List all contexts:
    - `k config get-contexts`
  - List current context:
    - `k config current-context`

- To see the Auth modes:
  - `k describe pod kube-apiserver -n kube-system`
    - Look for `--authorization-mode=`

- To create permissions for a User:
  - Role or ClusterRole:
    - `kubectl create clusterrole myuser-role --verb=get,list,watch --resource=nodes`
  - RoleBinding or ClusterRoleBindig:
    - `kubectl create clusterrolebinding myuser-role-binding --clusterrole=myuser-role --user=myuser`
  - Test it:
    - k get nodes --as myuser

- Security Context, run pod as non-root:
  - ```
      containers:
      - name: ....
        securityContext:
          runAsUser: 1000
          allowPrivilegeEscalation: false
    ```
  - Doc: <https://kubernetes.io/docs/tasks/configure-pod-container/security-context/> 