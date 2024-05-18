// Installation 

Prepare Docker Desktop and K8s enable or Docker with K8s.
After install Docker and K8s, install Skaffold by this link: https://skaffold.dev/docs/install/ .

We will use Skaffold for managing K8s and CI/CD local change in k8s. 

Then add ingress nginx by this command: "kubectl apply -f https://raw.githubusercontent.com/kubernetes/ingress-nginx/controller-v1.10.0/deploy/static/provider/aws/deploy.yaml"/
After the ingress, you must give 2 secret which is for JWT and Stripe key.
For example: 
 + "kubectl create secret generic jwt-secret --from-literal=JWT_KEY={put-jwt-secret-here}"
 + "kubectl create secret generic stripe-secret --from-literal STRIPE_KEY={put-the-secret-key-here}

// Note
- My Stripe key in code is hard code sorry for inconvenience, i might change later if i have free time.

// Execute
When everything's prepared go to console and run "skaffold -dev". The skaffold will pull the image from docker hub and also install Common package from my npm.

Wait till every image installed
+ You can access by the domain you manage in local (Which from C:\Windows\System32\Driver\etc\hosts) you can add "127.0.0.1 {your desire domain name}", in my case i change it into ticketing.dev and in k8s you must change in ingress.yaml
+ It will tell the web is not safe, this is because self signed certificate. Just ignore it by typing "thisisunsafe".

If there's no error, the web is working properly. 
