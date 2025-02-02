# media-cache-redis-state-sync
Microservice used to sync the state of the media cache storage with a redis metadata cache using minio event system and state reconciliation. (state reconciliation should be periodic and done at times of reduced load or metadata cache initalization))
# high level overview
**Note: this is an abstract generalization of how this service will work in theory and may change during actual implementation.
![media-cache-redis-state-sync excalidraw](https://github.com/user-attachments/assets/2a196d18-8b17-48b9-98d3-5e6c6b6aebd0)
