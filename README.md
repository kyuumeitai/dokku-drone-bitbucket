# How to use

Basically follow https://docs.drone.io/installation/bitbucket-cloud/single-machine/

In your dokku instance:
```
dokku apps:create drone

dokku storage:mount drone /var/run/docker.sock:/var/run/docker.sock
dokku storage:mount drone /var/lib/drone:/data

dokku config:set drone DRONE_BITBUCKET_CLIENT_ID={% your-bitbucket-key %}
dokku config:set drone DRONE_BITBUCKET_CLIENT_SECRET={% your-bitbucket-secret %}
dokku config:set drone DRONE_RUNNER_CAPACITY=2
dokku config:set drone DRONE_SERVER_HOST={% your-drone-server-host %}
dokku config:set drone DRONE_SERVER_PROTO={% your-drone-server-protocol %}

dokku domains:set drone drone.yoursite.com
dokku config:set --no-restart drone DOKKU_LETSENCRYPT_EMAIL=your@email

```
Change your settings properly.

Then, in your machine:
```
git clone https://github.com/kyuumeitai/dokku-drone-bitbucket.git
git remote add dokku dokku@example.com:dokku
```

Finally, put letsencrypt ssl to your installation

```
dokku letsencrypt drone
```