@4723112 ➜ /workspaces/WE-Docker/project_root (main) $ docker ps
CONTAINER ID   IMAGE                  COMMAND                  CREATED        STATUS          PORTS                                         NAMES
89c1cbdcf9a4   project_root-backend   "uvicorn main:app --…"   23 hours ago   Up 48 seconds   0.0.0.0:8000->8000/tcp, [::]:8000->8000/tcp   project_root-backend-1
ab7bd5750b7d   postgres:15            "docker-entrypoint.s…"   23 hours ago   Up 49 seconds   5432/tcp                                      project_root-db-1