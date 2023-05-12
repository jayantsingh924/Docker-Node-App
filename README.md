1. docker build .

2. docker image ls
REPOSITORY   TAG       IMAGE ID       CREATED         SIZE
<none>       <none>    055701b1b14b   3 minutes ago   1.01GB

3. docker image rm 055701b1b14b
Deleted: sha256:055701b1b14b89167dbae694d48573e6f72aa674acc7efc907da3562415e8228

4. docker image ls
REPOSITORY   TAG       IMAGE ID   CREATED   SIZE

5. docker build -t node_app_image .
                                                                    0.0s

6. docker image ls
REPOSITORY       TAG       IMAGE ID       CREATED         SIZE
node_app_image   latest    055701b1b14b   5 minutes ago   1.01GB

7. docker run -d --name node-app node_app_image
dc1476330b9f08660368e524e7c3d6cd44a26dd8a887008de9a1ebd4588f4e3d

8. docker ps
CONTAINER ID   IMAGE            COMMAND                  CREATED         STATUS         PORTS      NAMES
dc1476330b9f   node_app_image   "docker-entrypoint.s…"   5 seconds ago   Up 3 seconds   3000/tcp   node-app

9. docker rm node-app -f
node-app

10. docker ps
CONTAINER ID   IMAGE     COMMAND   CREATED   STATUS    PORTS     NAMES

11. docker run -p 3000:3000 -d --name node-app node_app_image
5cf03b73ebe5303516cd2fd6cb749ef28cd6185fd5f39481562aae7b4d1861eb

12. docker exec -it node-app bash

13. exit
