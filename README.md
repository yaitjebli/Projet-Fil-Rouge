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

```bash
docker-compose -f docker-compose-all-stack.yml up -d
```

```bash
[node1 STEP02-DEPLOYMENT]$ docker ps -a
CONTAINER ID   IMAGE                        COMMAND                  CREATED              STATUS                PORTS                                                      NAMES
cd62cad032a6   odoo:13.0                    "/entrypoint.sh odoo"    About a minute ago   Up 43 seconds         0.0.0.0:8069->8069/tcp, :::8069->8069/tcp, 8071-8072/tcp   odoo
7c6bb72da0a7   yaitjebli/ic-webapp:v1.0     "python app.py"          About a minute ago   Up About a minute     0.0.0.0:8080->8080/tcp, :::8080->8080/tcp                  ic-webapp
d1005195d987   postgres:10                  "docker-entrypoint.s…"   About a minute ago   Up About a minute     0.0.0.0:5432->5432/tcp, :::5432->5432/tcp                  postgres
9b13ef89fb78   dpage/pgadmin4               "/entrypoint.sh"         About a minute ago   Up About a minute     443/tcp, 0.0.0.0:5050->80/tcp, :::5050->80/tcp             pgadmin
```
Test your access to your webapp :
```bash
http://<host ip address>:8080
```
![image](https://user-images.githubusercontent.com/72947514/231658283-7701e5ea-5601-4b95-ad7a-e025473c5407.png)

Test your access to Odoo app :
```bash
http://<host ip address>:8069
```
![image](https://user-images.githubusercontent.com/72947514/231658596-7fb9e2a8-1ad1-496b-b321-b1cf9e4a3d27.png)

Enter required information to create the database and connect to the database :

![image](https://user-images.githubusercontent.com/72947514/231659621-5db74db4-8be6-4329-83c7-32c8a736de2e.png)


Test connexion to pgadmin home page :

![image](https://user-images.githubusercontent.com/72947514/231946123-77b3a689-30dc-4256-a24f-9ceb4ca3cdee.png)

and enter with credentendials given in the docker-compose file (docker-compose-all-stack.yml) :

![image](https://user-images.githubusercontent.com/72947514/231946758-2f151e35-5a16-44f4-903d-57a8c0cae76a.png)






