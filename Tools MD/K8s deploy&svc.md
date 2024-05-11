apiVersion: apps/v1
kind: Deployment
metadata:
  name: trainticket-app
spec:
  replicas: 2
  selector:
    matchLabels:
      app: trainticket-app
  template:
    metadata:
      labels:
        app: trainticket-app
    spec:
      containers:
        - name: trainticket
          image: 436312201622.dkr.ecr.ap-south-1.amazonaws.com/trainticket-ecr:latest
          ports:
            - containerPort: 8080
          env:
            - name: PORT
              value: "8080"
---
apiVersion: v1
kind: Service
metadata:
  name: trainticket-app
spec:
  type: LoadBalancer
  ports:
    - port: 80
      targetPort: 8080
  selector:
    app: trainticket-app
---
apiVersion: v1
kind: Pod
metadata:
  name: nginx
spec:
  containers:
  - name: nginx
    image: nginx:1.14.2
    ports:
    - containerPort: 80
	
-----
# Nginx Ingress Controller
ingress-resource.yml

apiVersion: networking.k8s.io/v1
kind: Ingress
metadata:
  name: my-ingress
spec:
  ingressClassName: nginx  
  rules:
  - host: www.myweb.com
    http:
      paths:
      - path: /
        pathtype: prefix
        backend: 
          service: 
            name: my-service
            port:
              number: 8080   	

----------------------------------------------------------------------------------------
3 tier architecture k8s manifest file

apiVersion: apps/v1
kind: Deployment
metadata:
  name: frontend
spec:
  selector:
    matchLabels:
      app: frontend
  replicas: 3
  template:
    metadata:
      labels:
        app: frontend
    spec:
      containers:
      - name: frontend
        image: my-frontend-image
        ports:
        - containerPort: 80
        env:
        - name: BACKEND_ENDPOINT
          value: "backend-svc:8080"
		  
---
apiVersion: v1
kind: Service
metadata:
  name: frontend-svc
spec:
  selector:
    app: frontend
  ports:
  - name: http
    protocol: TCP
    port: 80
    targetPort: 80
  type: LoadBalancer		  
  
---
apiVersion: apps/v1
kind: Deployment
metadata:
  name: backend
spec:
  selector:
    matchLabels:
      app: backend
  replicas: 2
  template:
    metadata:
      labels:
        app: backend
    spec:
      containers:
      - name: backend
        image: my-backend-image
        ports:
        - containerPort: 8080
        env:
        - name: DATABASE_ENDPOINT
          value: "database-svc:3306"
		  
---
apiVersion: v1
kind: Service
metadata:
  name: backend-svc
spec:
  selector:
    app: backend
  ports:
  - name: http
    protocol: TCP
    port: 8080
    targetPort: 8080
  type: ClusterIP		  
  
---
apiVersion: apps/v1
kind: Deployment
metadata:
  name: database
spec:
  selector:
    matchLabels:
      app: database
  replicas: 1
  template:
    metadata:
      labels:
        app: database
    spec:
      containers:
      - name: database
        image: my-database-image
        ports:
        - containerPort: 3306
		
---
apiVersion: v1
kind: Service
metadata:
  name: database-svc
spec:
  selector:
    app: database
  ports:
  - name: mysql
    protocol: TCP
    port: 3306
    targetPort: 3306
  type: ClusterIP
---------------------------------------------------------------------------------------------

ConfigMap:- In Kubernetes, a ConfigMap is an object used to store configuration data in key-value pairs. It is used to separate configuration data from the application code, allowing the configuration to be updated without changing the application code.
         Here is an example of a "ConfigMap" that could be used to store database connection information for an application:

apiVersion: v1
kind: ConfigMap
metadata:
  name: db-config
data:
  DB_NAME: my_database
  DB_USER: my_username
  DB_PASSWORD: my_password
  DB_HOST: db.example.com
  DB_PORT: "5432"
		  
In this example, the "ConfigMap" is named "db-config" and contains five key-value pairs, where each key represents a database configuration parameter such as the database name, username, password, hostname, and port.	

This "ConfigMap" can then be used by an application by defining an environment variable or a configuration file that references these keys. For example, to use the "DB_USER" key in an environment variable, you could define it as follows:

apiVersion: apps/v1
kind: Deployment
metadata:
  name: my-app
spec:
  replicas: 3
  template:
    metadata:
      labels:
        app: my-app
    spec:
      containers:
      - name: my-app
        image: my-app:latest
        env:
        - name: DB_USER
          valueFrom:
            configMapKeyRef:
              name: db-config
              key: DB_USER

In this example, the "DB_USER" environment variable is being set to the value of the "DB_USER" key in the "db-config" "ConfigMap". This allows the application to access the database connection information without having to hardcode it into the application code.
---------------------------------------------------------------------------------------------

Secrets:- Kubernetes, 'Secrets' is an object used to store sensitive data such as passwords, API keys, and other confidential information in an encrypted format. It is similar to 'ConfigMaps', but the data is stored in an encrypted format.	  

Here is an example of a 'Secrets' that could be used to store a password for a database:

apiVersion: v1
kind: Secret
metadata:
  name: db-password
type: Opaque
data:
  password: cGFzc3dvcmQ=
  
  In this example, the 'Secret' is named 'db-password' and contains a single key-value pair, where the key is 'password' and the value is 'cGFzc3dvcmQ=', which is the Base64-encoded version of the plaintext password "password".

This 'Secret' can then be used by an application by defining an environment variable or a configuration file that references the key. For example, to use the 'password' key in an environment variable, you could define it as follows:

apiVersion: apps/v1
kind: Deployment
metadata:
  name: my-app
spec:
  replicas: 3
  template:
    metadata:
      labels:
        app: my-app
    spec:
      containers:
      - name: my-app
        image: my-app:latest
        env:
        - name: DB_PASSWORD
          valueFrom:
            secretKeyRef:
              name: db-password
              key: password

In this example, the 'DB_PASSWORD' environment variable is being set to the value of the 'password' key in the 'db-password' 'Secret'. This allows the application to access the database password without having to hardcode it into the application code.

----------------------------------------------------------------------------------------------

k8s RBAC Authorization: RBAC stands for Role-Based Access Control. It is security method that is used for restricting access to users on the Kubernetes cluster-wide.

https://kubernetes.io/docs/reference/access-authn-authz/rbac/

Role example: A Role always sets permissions within a particular namespace; when you create a Role, you have to specify the namespace it belongs in. 
Here's an example Role in the "default" namespace that can be used to grant read access to pods:

Role.yml
-----------
apiVersion: rbac.authorization.k8s.io/v1
kind: Role
metadata:
  namespace: default
  name: pod-reader
rules:
- apiGroups: [""]  # "" indicates the core API group
  resources: ["pods"]
  verbs: ["get", "watch", "list"]
  
  ----------------------------------------------------------------------------------------------------
  
  RoleBinding example: A role binding grants the permissions defined in a role to a user or set of users. It holds a list of subjects (users, groups, or service accounts), and a reference to the role being granted. A RoleBinding grants permissions within a specific namespace whereas a ClusterRoleBinding grants that access cluster-wide.
  
  Here is an example of a RoleBinding that grants the "pod-reader" Role to the user "jane" within the "default" namespace. This allows "jane" to read pods in the "default" namespace.
  
  RoleBinding.yml
  -------------------
  apiVersion: rbac.authorization.k8s.io/v1
# This role binding allows "jane" to read pods in the "default" namespace.
# You need to already have a Role named "pod-reader" in that namespace.
kind: RoleBinding
metadata:
  name: read-pods
  namespace: default
subjects:
# You can specify more than one "subject"
- kind: User
  name: jane # "name" is case sensitive
  apiGroup: rbac.authorization.k8s.io
roleRef:
  # "roleRef" specifies the binding to a Role / ClusterRole
  kind: Role #this must be Role or ClusterRole
  name: pod-reader # this must match the name of the Role or ClusterRole you wish to bind to
  apiGroup: rbac.authorization.k8s.io
  -----------------------------------------------------------------------------------------
  # ClusterRole

apiVersion: rbac.authorization.k8s.io/v1
kind: ClusterRole
metadata:
  name: secret-reader
rules:
- apiGroups: [""]
  resources: ["secrets"]  # objects is "secrets"
  verbs: ["get", "watch", "list"]
--------------------------------------------------------------------------------------------
 # ClusterRoleBinding

apiVersion: rbac.authorization.k8s.io/v1
kind: RoleBinding
metadata:
  name: read-secrets
  namespace: development
subjects:
- kind: User
  name: dave # Name is case sensitive
  apiGroup: rbac.authorization.k8s.io
roleRef:
  kind: ClusterRole
  name: secret-reader
  apiGroup: rbac.authorization.k8s.io 
