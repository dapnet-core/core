# Docker-based DAPNET node setup

To run the "old" setup using [web](https://github.com/dapnet-core/web/tree/vuetify) as frontend, checkout [this commit](https://github.com/dapnet-core/core/commit/af04eaedaf9bcd6439e8d05a289ffe30ea89f84c)
## Requirements

- Docker
- Docker Compose

## Startup Procedure

1. Copy `config/config.env.example` into `config/config.env` and enter your node settings
2. Run

```bash
docker-compose up
```

3. If all 5 services started, rabbitmq will repeatedly emit errors. To fix them, add your node to [CouchDB](http://localhost:5984/_utils/#database/nodes/_new). Login credentials are set in the `config.env` file from step one. Replace the values in the following template, then paste it into the 'New document' form:

```JSON
{
  "_id": "<NODE_NAME>",
  "auth_key": "<NODE_AUTHKEY>"
}
```

4. After that, ask someone else who runs a node to add your node so replication can begin.

## Development
### Frontend
Set it up manually and use `http://localhost:888` as api server as described in the README inside the frontend folder.
### Api service
Its easiest to just use the api container itself using VSCode's [Attach to Container](https://code.visualstudio.com/docs/remote/attach-container) feature. The files are in `/app/` and hot reloading works (from outside the container too), so you don't have to restart the conatiner to apply changes.
