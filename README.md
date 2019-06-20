# How to use

Basically follow https://docs.drone.io/installation/bitbucket-cloud/single-machine/

```
dokku apps:create drone

dokku storage:mount /var/run/docker.sock:/var/run/docker.sock
dokku storage:mount /var/lib/drone:/data

dokku proxy:ports-add drone http:80:80
dokku proxy:ports-add drone http:443:443

dokku config:set drone DRONE_BITBUCKET_CLIENT_ID={% your-bitbucket-key %}
dokku config:set drone DRONE_BITBUCKET_CLIENT_SECRET={% your-bitbucket-secret %}
dokku config:set drone DRONE_RUNNER_CAPACITY=2
dokku config:set drone DRONE_SERVER_HOST={% your-drone-server-host %}
dokku config:set drone DRONE_SERVER_PROTO={% your-drone-server-protocol %}

dokku config:set --no-restart drone DOKKU_LETSENCRYPT_EMAIL=alex@lunamedia.cl

```

