# Projet-Fil-Rouge
Projet de mise en place d'un pipeline CI-CD dans le cadre de la formation DevOps [eazytraining.fr]

STEP 01 - containerization
--------------------------
```
[node1 STEP01-IMAGE_BUILD]$ docker build -t ic-webapp:1.0 .
```

```
[node1 STEP01-IMAGE_BUILD]$ docker run -d --name test-webapp -p 8084:8080 ic-weba
99cfac5d59e676530f2cb74d79bacd9a727767f2bf56f67d7a4005a3e08f3418
```

```
[node1 STEP01-IMAGE_BUILD]$ docker ps -a | grep test-webapp
99cfac5d59e6   ic-webapp:1.0    "python app.py"  13 seconds ago   Up 10 seconds   0.0.0.0:8084->8080/tcp, :::8084->8080/tcp   test-webapp
```
