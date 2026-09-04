```
User's browser
      |
      | http://127.0.0.1:<tunnel-port>
      v
mongo-express-service
      |
      | port 8081
      v
mongo-express pod
      |
      | mongodb://mongodb-service:27017
      v
mongodb-service
      |
      | port 27017
      v
MongoDB pod
```

1. `mongo-secret.yaml` stores the MongoDB root username and password as a Kubernetes Secret. The values are base64 encoded, not plain text. `mongo-deployment.yaml` and `mongo-express.yaml` refer to the secret by `name: mongodb-secret`.
2. `mongo-deployment.yaml` creates the MongoDB pod and service. The pod uses the `mongo:latest` image and sets the environment variables for the root username and password from the secret. The service exposes port 27017 for MongoDB and labels pod as `app: mongodb`.
3. `mongo-service.yaml` creates an internal Kubernetes service for MongoDB, allowing other pods in the cluster to communicate with it using the service name `mongodb-service` on port 27017.
4. `mongo-configmap.yaml` contains non-sensitive configuration values for the Mongo Express application.
5. `mongo-express.yaml` creates a Mongo Express application and external service. A LoadBalancer service is used to expose the application outside a Kubernetes cluster. 

Flow
1. User access external IP, Minikube tunnel forwards local traffic to `mongo-express-service` on port 8081.
2. `mongo-express-service` recieves HTTP request on port 8081 and selector searches for pods with label `app: mongo-express`, forwards request to `mongo-express` pod.
3. Traffic reaches `mongo-express` pod, Mongo Express checks browser credentials `ME_CONFIG_BASICAUTH_USERNAME` and
`ME_CONFIG_BASICAUTH_PASSWORD`
4. After successful browser authentication, Mongo Express connects to `mongodb-service:27017`
5. `mongodb-service` receives request on port 27017, selector searches for pods with label `app: mongodb`, forwards request to `mongodb` pod.