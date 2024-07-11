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