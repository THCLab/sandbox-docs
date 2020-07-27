# sandbox-docs

Official documentation for DDE sandbox environment

## Structure

```sh
.
├── sandbox
│   ├── nginx
│   │   ├── conf.d
│   │   └── nginx.conf
│   ├── services
│   │   ├── oca-data-vault
│   │   ├── oca-editor
│   │   ├── oca-repository
│   │   │   └── es-config/mappings
│   │   └── tda
│   │       ├── agent
│   │       ├── agent-web-client
│   │       └── von-network
│   └── docker-compose.yml
└── sandbox-manager
    ├── config
    ├── sandboxes-data
    ├── templates
    └── docker-compose.yml
```

### [Sandbox Manager](https://github.com/THCLab/sandbox-manager)

* SANDBOX_PATH indicates on `sandbox-manager/sandboxes-data` directory
* `sandbox-manager:/usr/src/app/nginx_conf` is linked with `sandbox/nginx/conf.d` with volume defined in `sandbox-manager/docker-compose.yml`
* cron sends `GET /api/v1/stop-overdue` request  every 5 minutes

### Sandbox services

[**tda/von-network**](https://github.com/bcgov/von-network)  
`./manage start` - starts ledger  
`./manage stop` - stops ledger  
`./manage down` - stops and cleans ledger data  
`./manage logs` - prints ledger logs

[**oca-repository**](https://github.com/THCLab/odca-search-engine)
* on startup loads ElasticSearch mappings defined in es-config/mappings

[**oca-editor**](https://github.com/THCLab/oca-editor) and [**tda/agent-web-client**](https://github.com/THCLab/aries-toolbox) 
* `dist` directories are linked to nginx container with volumes defined in `sandbox/docker-compose.yml`
* when updating docker image version - be sure to remove `sandbox_toolbox_dist`/`sandbox_editor_dist` volume before

## Running it up

1. Start von-network ledger with `./sandbox/services/tda/von-network/manage start`
1. Start sandbox manager with `docker-compose -f ./sandbox-manager/docker-compose.yml up -d`
1. Start sandbox services with `docker-compose -f ./sandbox/docker-compose.yml up -d`
