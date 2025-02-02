# media-cache-redis-state-sync
Microservice used to sync the state of the media cache storage with a redis metadata cache using minio event system and state reconciliation. (state reconciliation should be periodic and done at times of reduced load or metadata cache initalization))
# abstract overview
**Note: this is an abstract generalization of how this service will work in theory and may change during actual implementation.
![media-cache-redis-state-sync excalidraw](https://github.com/user-attachments/assets/2a196d18-8b17-48b9-98d3-5e6c6b6aebd0)
# notes
+ Minio uses multiple transport mechinisms for its event system, including but not limited to HTTP, Redis PUB/SUB and KAFKA, simple/poc implementations can use HTTP, but more reliable infastructure may be better suited using kafka
+ State reconciliation occurances should be balanced in a way that desyncs are rare and quickly ammended but not too occurant that it causes system strain when unnecessary, the event stream can handle most state syncing more effiecently
+ Optimizations can easily be made to state reconcilation, through direct integration with minio and related system diagnostics stacks allowing intelligent scheduling decisions that perform reconciliation at times of reduced related system load
+ Many race/data conflicts can occur due to innate networking and system delays between components, EXTREME CONSIDERATION IS REQUIRED!!! Ensure that all actions to redis are transactional/atomic and aware of prior and proceeding actions across sync service instances to properly reflect state
