<h1 align="center">🌐 Full Stack ChatApp Deployment on Kubernetes (Minikube)</h1>

<p align="center">
  A production-grade 3-tier application deployed on Minikube using Docker & Kubernetes with MongoDB, Node.js/Express backend, and React frontend.
</p>

<hr>

<h2>🚀 Tech Stack</h2>
<ul>
  <li><strong>Frontend</strong>: React.js</li>
  <li><strong>Backend</strong>: Node.js + Express</li>
  <li><strong>Database</strong>: MongoDB</li>
  <li><strong>Containerization</strong>: Docker</li>
  <li><strong>Orchestration</strong>: Kubernetes (Minikube)</li>
</ul>

<hr>

<h2>📄 Project Overview</h2>
<p>
  This project demonstrates the deployment of a scalable full-stack chat application using a 3-tier architecture:
</p>
<ul>
  <li><strong>Tier 1: Frontend</strong> - React.js single-page application</li>
  <li><strong>Tier 2: Backend</strong> - Node.js/Express APIs</li>
  <li><strong>Tier 3: Database</strong> - MongoDB for persistent storage</li>
</ul>
<p>
  The setup includes Kubernetes objects like Deployments, Services, Persistent Volumes, Secrets, Namespaces, and Ingress. Ideal for DevOps and Cloud-native learning.
</p>

<hr>

<h2>📦 Docker Image Setup</h2>
<ol>
  <li>Build the backend image</li>
  <pre><code>docker build -t &lt;your-dockerhub-username&gt;/chatapp-backend:latest ./backend</code></pre>
  
  <li>Build the frontend image</li>
  <pre><code>docker build -t &lt;your-dockerhub-username&gt;/chatapp-frontend:latest ./frontend</code></pre>
  
  <li>Push images to Docker Hub</li>
  <pre><code>
docker push &lt;your-dockerhub-username&gt;/chatapp-backend:latest
docker push &lt;your-dockerhub-username&gt;/chatapp-frontend:latest
  </code></pre>
</ol>

<hr>

<h2>🔧 Kubernetes Setup (Minikube)</h2>

<ol>
  <li>Start Minikube</li>
  <pre><code>minikube start</code></pre>

  <li>Enable ingress addon</li>
  <pre><code>minikube addons enable ingress</code></pre>

  <li>Create Namespace</li>
  <pre><code>kubectl apply -f namespace.yaml</code></pre>

  <li>Apply Secrets</li>
  <pre><code>kubectl apply -f secret.yaml</code></pre>

  <li>Apply Persistent Volume & Claim</li>
  <pre><code>
kubectl apply -f pv.yaml
kubectl apply -f pvc.yaml
  </code></pre>

  <li>Deploy MongoDB</li>
  <pre><code>
kubectl apply -f mongodb-deployment.yaml
kubectl apply -f mongo-svc.yaml
  </code></pre>

  <li>Deploy Backend & Frontend</li>
  <pre><code>
kubectl apply -f deployment-backend.yaml
kubectl apply -f backend-svc.yaml

kubectl apply -f deployment-frontend.yaml
kubectl apply -f frontend-svc.yaml
  </code></pre>

  <li>Apply Ingress</li>
  <pre><code>kubectl apply -f ingress.yaml</code></pre>

  <li>Access Minikube Ingress</li>
  <pre><code>minikube tunnel</code></pre>
</ol>

<hr>

<h2>🌐 Port Forwarding (Optional)</h2>
<pre><code>
kubectl port-forward svc/chatapp-backend 5000:5000 -n chatapp
kubectl port-forward svc/chatapp-frontend 3000:3000 -n chatapp
kubectl port-forward svc/mongodb-service 27017:27017 -n chatapp
</code></pre>

<hr>

<h2>📂 Directory Structure</h2>
<pre><code>full-stack_chatApp/kubernetes
├── backend-svc.yaml
├── deployment-backend.yaml
├── deployment-frontend.yaml
├── frontend-svc.yaml
├── mongo-svc.yaml
├── mongodb-deployment.yaml
├── namespace.yaml
├── pv.yaml
├── pvc.yaml
├── secret.yaml
└── ingress.yaml</code></pre>

<hr>

<h2>🎯 Learning Outcomes</h2>
<ul>
  <li>Docker image creation and management</li>
  <li>Working with Persistent Volumes and Claims</li>
  <li>Creating and using Kubernetes Secrets securely</li>
  <li>Ingress setup and domain routing in Minikube</li>
</ul>

<hr>

<h2>📚 Useful Commands</h2>
<pre><code>
kubectl get all -n chatapp
kubectl logs &lt;pod-name&gt; -n chatapp
kubectl describe pod &lt;pod-name&gt; -n chatapp
kubectl delete -f &lt;file.yaml&gt;
kubectl exec -it &lt;pod-name&gt; -n chatapp -- bash
</code></pre>

<hr>

<h2>📷 Screenshots / Diagrams</h2>
<p><strong>App UI Preview:</strong></p>


<p><strong>Architecture Diagram:</strong></p>
<p align="center">
  <img src="https://raw.githubusercontent.com/p-udaykiran/full-stack_chatApp/refs/heads/main/frontend/public/arc.png" alt="Architecture Diagram" width="800"/>
</p>

<hr>

<h2>📌 Author</h2>
<p>
  <strong>Uday Kiran</strong><br>
  Cloud & DevOps Enthusiast
</p>
