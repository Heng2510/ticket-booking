// Installation 

Prepare Docker and Kubernetes
Install Docker Desktop and enable Kubernetes (or use Docker with K8s enabled).
After that, install Skaffold following the instructions here: [Skaffold Install.](https://skaffold.dev/docs/install/)
We use Skaffold to manage local Kubernetes deployments and CI/CD workflows.

Set up Ingress and Secrets
Add ingress-nginx:
+ kubectl apply -f https://raw.githubusercontent.com/kubernetes/ingress-nginx/controller-v1.10.0/deploy/static/provider/aws/deploy.yaml
Create the required secrets for JWT and Stripe:
+ kubectl create secret generic jwt-secret --from-literal=JWT_KEY={your-jwt-key}
+ kubectl create secret generic stripe-secret --from-literal=STRIPE_KEY={your-stripe-key}

// Execute

When everything's prepared go to console and run "skaffold -dev". 
Skaffold will pull the necessary Docker images and install required npm packages.
Wait until all images and packages are ready.

Access the application locally:
Add your desired domain to your hosts file (C:\Windows\System32\drivers\etc\hosts on Windows).
Example: 127.0.0.1 ticketing.dev
Make sure the same domain is updated in ingress.yaml.

Ignore self-signed certificate warnings:
When opening the site, your browser may warn that the connection is not secure.
On Chrome, type 'thisisunsafe' to proceed.

If there are no errors, the application should be up and running successfully.
