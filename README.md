# Projet-Fil-Rouge
Projet de mise en place d'un pipeline CI-CD dans le cadre de la formation DevOps [eazytraining.fr]

STEP 01 - containerization
--------------------------

```
[node1 STEP01-IMAGE_BUILD]$ docker ps -a | grep test-webapp
99cfac5d59e6   ic-webapp:1.0    "python app.py"  13 seconds ago   Up 10 seconds   0.0.0.0:8084->8080/tcp, :::8084->8080/tcp   test-webapp
```
