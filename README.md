

D:\Learning\Docker\node>docker build .
2023/05/13 03:25:50 http2: server: error reading preface from client //./pipe/docker_engine: file has already been closed
[+] Building 1.2s (10/10) FINISHED
 => [internal] load build definition from Dockerfile                                                               0.1s
 => => transferring dockerfile: 153B                                                                               0.0s
 => [internal] load .dockerignore                                                                                  0.1s
 => => transferring context: 2B                                                                                    0.0s
 => [internal] load metadata for docker.io/library/node:18                                                         0.9s
 => [internal] load build context                                                                                  0.1s
 => => transferring context: 49.35kB                                                                               0.1s
 => [1/5] FROM docker.io/library/node:18@sha256:3f567a26b6b6d601fb2b168d4f987b50697617ead15bfc0e0152e600ac48d0fe   0.0s
 => CACHED [2/5] WORKDIR /app                                                                                      0.0s
 => CACHED [3/5] COPY package.json .                                                                               0.0s
 => CACHED [4/5] RUN npm install                                                                                   0.0s
 => CACHED [5/5] COPY . ./                                                                                         0.0s
 => exporting to image                                                                                             0.0s
 => => exporting layers                                                                                            0.0s
 => => writing image sha256:055701b1b14b89167dbae694d48573e6f72aa674acc7efc907da3562415e8228                       0.0s

D:\Learning\Docker\node>docker image ls
REPOSITORY   TAG       IMAGE ID       CREATED         SIZE
<none>       <none>    055701b1b14b   3 minutes ago   1.01GB

D:\Learning\Docker\node>docker image rm 055701b1b14b
Deleted: sha256:055701b1b14b89167dbae694d48573e6f72aa674acc7efc907da3562415e8228

D:\Learning\Docker\node>docker image ls
REPOSITORY   TAG       IMAGE ID   CREATED   SIZE

D:\Learning\Docker\node>docker build -t node_app_image .
[+] Building 2.2s (11/11) FINISHED
 => [internal] load build definition from Dockerfile                                                                  0.0s
 => => transferring dockerfile: 153B                                                                                  0.0s
 => [internal] load .dockerignore                                                                                     0.1s
 => => transferring context: 2B                                                                                       0.0s
 => [internal] load metadata for docker.io/library/node:18                                                            2.0s
 => [auth] library/node:pull token for registry-1.docker.io                                                           0.0s
 => [1/5] FROM docker.io/library/node:18@sha256:3f567a26b6b6d601fb2b168d4f987b50697617ead15bfc0e0152e600ac48d0fe      0.0s
 => [internal] load build context                                                                                     0.1s
 => => transferring context: 49.35kB                                                                                  0.0s
 => CACHED [2/5] WORKDIR /app                                                                                         0.0s
 => CACHED [3/5] COPY package.json .                                                                                  0.0s
 => CACHED [4/5] RUN npm install                                                                                      0.0s
 => CACHED [5/5] COPY . ./                                                                                            0.0s
 => exporting to image                                                                                                0.0s
 => => exporting layers                                                                                               0.0s
 => => writing image sha256:055701b1b14b89167dbae694d48573e6f72aa674acc7efc907da3562415e8228                          0.0s
 => => naming to docker.io/library/node_app_image                                                                     0.0s

D:\Learning\Docker\node>docker image ls
REPOSITORY       TAG       IMAGE ID       CREATED         SIZE
node_app_image   latest    055701b1b14b   5 minutes ago   1.01GB

D:\Learning\Docker\node>docker run -d --name node-app node_app_image
dc1476330b9f08660368e524e7c3d6cd44a26dd8a887008de9a1ebd4588f4e3d

D:\Learning\Docker\node>docker ps
CONTAINER ID   IMAGE            COMMAND                  CREATED         STATUS         PORTS      NAMES
dc1476330b9f   node_app_image   "docker-entrypoint.s…"   5 seconds ago   Up 3 seconds   3000/tcp   node-app

D:\Learning\Docker\node>docker rm node-app -f
node-app

D:\Learning\Docker\node>docker ps
CONTAINER ID   IMAGE     COMMAND   CREATED   STATUS    PORTS     NAMES

D:\Learning\Docker\node>docker run -p 3000:3000 -d --name node-app node_app_image
5cf03b73ebe5303516cd2fd6cb749ef28cd6185fd5f39481562aae7b4d1861eb

D:\Learning\Docker\node>