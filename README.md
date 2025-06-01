# Demo Project: Deploying MongoDB and Mongo Express on Kubernetes

This project demonstrates how to deploy a MongoDB database along with Mongo Express, a web-based MongoDB admin interface, in a Kubernetes environment. It covers essential Kubernetes concepts including Pods, Services, Secrets, Deployments, and ConfigMaps.

## Project Structure

- **Deploying MongoDB and Mongo Express**
This project consists of two primary components:
    - **MongoDB**: A NoSQL document-oriented database.
    - **Mongo Express**: A web-based administrative interface for MongoDB.

- **MongoDB Pod**
A dedicated Pod is configured to run the MongoDB container. This Pod ensures MongoDB is running as a standalone service within the cluster.

- **Secret**  
Kubernetes Secrets are used to securely store sensitive data such as the MongoDB root username and password. These are later referenced by the MongoDB and Mongo Express containers.

- **MongoDB Internal Service**  
An internal Kubernetes Service is created to expose MongoDB within the cluster. This allows other Pods (like Mongo Express) to access the database without exposing it to the public.

- **Deployment Service and ConfigMap**  
    - **Deployment**: Manages the deployment of Mongo Express, ensuring high availability and scalability.
    - **ConfigMap**: Stores non-sensitive configuration data for Mongo Express, such as MongoDB connection details.

- **Mongo Express External Service**  
A Kubernetes Service of type `NodePort` or `LoadBalancer` is used to expose Mongo Express externally, allowing access through a browser.

## How to Use

### Prerequisites
- A Kubernetes cluster (Minikube, Kind, GKE, etc.)
- `kubectl` configured to access your cluster

### Deployment Steps

- **Apply Secrets**
    - `kubectl apply -f secret.yaml`
- **Deploy MongoDB**
    - `kubectl apply -f mongodb.yaml`
    - `kubectl apply -f mongodb-service.yaml` (Included on `mongodb.yaml`)
- **Deploy Mongo Express**
    - `kubectl apply -f configmap.yaml`
    - `kubectl apply -f mongo-express.yaml`
    - `kubectl apply -f mongo-express-service.yaml` (Included on `mongo-express.yaml`)

## Accessing Mongo Express
- If using `Minikube`:
    - `minikube service mongo-express-service`
- If using `LoadBalancer`, get the external IP:
    - `kubectl get svc mongo-express-service`

## troubleshooting
- Issue mongo-express or mongo-db pods not starting or giving an error
    - Use the `docker` driver for `minikube` by simply running `minikube` start without specifying the driver
    - Simple installation guide for [Minikube](https://minikube.sigs.k8s.io/docs/start/)

## 🧑‍💻 Developer Setup
- Clone the repository:
- git clone ``

## 👨‍💻 Author Amitesh Singh – [GitHub](https://github.com/amitesh786)
- Feel free to contribute or suggest improvements! 🙌
