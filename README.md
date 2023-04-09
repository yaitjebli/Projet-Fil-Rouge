# Projet-Fil-Rouge
Projet de mise en place d'un pipeline CI-CD dans le cadre de la formation DevOps [eazytraining.fr]

--------------------------
STEP 01 - containerization
--------------------------

```bash
[node1 STEP01-IMAGE_BUILD]$ docker build -t ic-webapp:1.0 .
```

```bash
[node1 STEP01-IMAGE_BUILD]$ docker run -d --name test-ic-webapp -p 8084:8080 ic-webapp:1.0
99cfac5d59e676530f2cb74d79bacd9a727767f2bf56f67d7a4005a3e08f3418
```

```bash
[node1 STEP01-IMAGE_BUILD]$ docker ps -a | grep test-ic-webapp
99cfac5d59e6   ic-webapp:1.0    "python app.py"  13 seconds ago   Up 10 seconds   0.0.0.0:8084->8080/tcp, :::8084->8080/tcp   test-ic-webapp
```

We have to check if the application works properly by entring the following address in the browser address bar :

```bash
http://<host ip address>:8084
```

![image](https://user-images.githubusercontent.com/72947514/230758929-43cb1adb-eccc-446d-a973-592d1109a387.png)



---------------------------------------------------------
STEP 02 - Applications deployment on a Kubernetes cluster
---------------------------------------------------------
