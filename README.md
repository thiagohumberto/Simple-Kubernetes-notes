# Simple-Kubernetes-notes

Simple notes of how to deploy in Kubernetes.

1. Get your cluster `kubeconfig.yaml` from your provder, it should be available in cluster configs.

2. Install kubectl, cli command line.

    `curl -LO "https://dl.k8s.io/release/$(curl -L -s https://dl.k8s.io/release/stable.txt)/bin/linux/amd64/kubectl"
`

3. I suppose that you have some knowledgment about Docker, if not, my suggestion is to research how Docker works before the next steps, otherwise build you app image, with the following command:

    `docker build -t your-user/repository-name:your-app-tag .`

4. Login into docker hub

    `docker login -u your-user`

5. Push your app image to registry

    `docker push your-user/app-demo:demo-v1`

6. Create a Docker HUB secret for Docker hub login.

    `kubectl create secret docker-registry dockerhub-secret \
  --docker-server=https://index.docker.io/v1/ \
  --docker-username=your-user \
  --docker-password=xxxxxxxxxxxxxxxxxxxxxxx \
  --docker-email=your@emal.com`

7. Deploy, the yaml files are here in this same directory

   `kubectl apply -f service.yaml`

   `kubectl apply -f deployment.yaml`

8. Check your service IP (internal and external)

    `kubectl get svc hello-world-node`