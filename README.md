# ddhub-client-gateway-api

![Version: 0.2.0](https://img.shields.io/badge/Version-0.2.0-informational?style=flat-square) ![Type: application](https://img.shields.io/badge/Type-application-informational?style=flat-square) ![AppVersion: 0.4.0](https://img.shields.io/badge/AppVersion-0.4.0-informational?style=flat-square)

A Helm chart for Kubernetes

## Requirements

| Repository | Name | Version |
|------------|------|---------|
| https://aemocontainerregistry.azurecr.io/helm/v1/repo | ddhub-client-gateway-ui | 0.0.1 |

## Values

| Key | Type | Default | Description |
|-----|------|---------|-------------|
| affinity | object | `{}` |  |
| autoscaling.enabled | bool | `false` |  |
| autoscaling.maxReplicas | int | `100` |  |
| autoscaling.minReplicas | int | `1` |  |
| autoscaling.targetCPUUtilizationPercentage | int | `80` |  |
| clientgateway.config.cache_server_url | string | `"https://identitycache-staging.energyweb.org/v1"` | Sets the Energy Web IAM cache server URL, used to cache identities (as it can be expensive to rely only on querying smart contract data). |
| clientgateway.config.chain_id | int | `73799` | Sets the chain ID of the blockchain network. Options: 73799 (Volta), 246 (EWC) |
| clientgateway.config.db_name | string | `"local.db"` | Sets the database name / path for channel configurations. |
| clientgateway.config.dsb_base_url | string | `"http://ddhub-messagebroker-proxy-dev.ddhub-dev.svc"` | The URL of the DSB Message Broker you want to connect to. Trailing / allowed. |
| clientgateway.config.event_server_url | string | `"https://identitycache-staging.energyweb.org/"` | Sets the Energy Web IAM events server URL, used to receive notification of approved DSB role claims. |
| clientgateway.config.events_emit_mode | string | `"BULK"` | Defines the format for messages pushed over a real-time communication channel. If bulk mode is chosen, messages will be sent as an array. At every 1 second interval, the gateway will emit an array of the latest messages received. If single mode is chosen, messages will be sent individually. Options: BULK, SINGLE |
| clientgateway.config.events_max_per_second | int | `2` | Defines how many events should be pushed per second, regardless of mode chosen (see above). |
| clientgateway.config.node_env | string | `"test"` | Sets the application environment. |
| clientgateway.config.opentelemetry_enabled | bool | `false` | Sets to enable opentelemetry. |
| clientgateway.config.opentelemetry_exporter | string | `""` | Sets opentelemetry exporter. enum ["ZIPKIN"] |
| clientgateway.config.opentelemetry_otel_collector_url | string | `""` | Sets opentelemetry collector url. |
| clientgateway.config.opentelemetry_otel_environment | string | `""` | Sets opentelemetry telemetry environment. default: "local" |
| clientgateway.config.opentelemetry_otel_ignored_routes | string | `""` | Sets opentelemetry collector ignored routes. comma seperated, default: "health,api/v2/health" |
| clientgateway.config.opentelemetry_otel_service_name | string | `""` | Sets opentelemetry telemetry service name. default: "ddhub-client-gateway" |
| clientgateway.config.parent_namespace | string | `"dsb.apps.energyweb.iam.ewc"` | Sets the Energy Web IAM application namespace. DSB related roles, such as user and messagebroker should fall under this namespace. |
| clientgateway.config.port | int | `3333` | Define the port the gateway will run on. |
| clientgateway.config.rpc_url | string | `"https://volta-rpc.energyweb.org/"` | Sets the blockchain RPC node to connect to retreive state from and submit transactions to. Should match the network given in CHAIN_ID. |
| clientgateway.config.secret_engine | string | `"vault"` | Sets the secret engine for storing DID private key. it can be Vault/AWS SSM/Azure KeyVault/GCP Secret Manager. |
| clientgateway.config.secret_engine_endpoint | string | `"http://vault.ddhub-dev.svc:8200"` | Sets the secret engine endpoint. the secret engine server URL. |
| clientgateway.config.websocket | string | `"NONE"` | Select WebSocket mode depending on architecture (i.e. preference for inbound or outbound connections). By default, the gateway will run a WebSocket server on /events. However, it can also operate as a client with additional configuration (see below). Alternatively, this functionality can be turned off. Options: SERVER, CLIENT, NONE |
| clientgateway.config.websocket_protocol | string | `""` | Sets the protocol the WebSocket client should request access to. Acceptable protocols are defined by the WebSocket server, however, this can also be left undefined. Note that if WEBSOCKET is set to SERVER this variable is ignored. The server will only accept connection requests on the dsb-messages protocol. |
| clientgateway.config.websocket_reconnect | bool | `false` | Define whether the WebSocket client should reconnect on connection error/close. |
| clientgateway.config.websocket_reconnect_max_retries | int | `10` | Define how many times the WebSocket client should attempt reconnection with the server upon receving connection error/close. |
| clientgateway.config.websocket_reconnect_timeout | int | `10000` | Define the interval between receiving a connection error/close and attempting to reconnect, in milliseconds. |
| clientgateway.config.websocket_url | string | `""` | Sets the URL of the WebSocket server the client should try to connect to. Required if WEBSOCKET is set to CLIENT. |
| clientgateway.scheduler.appConfig.DID_AUTH_URL | string | `"http://ddhub-messagebroker-proxy-dev.ddhub-dev.svc"` |  |
| clientgateway.scheduler.appConfig.DID_REGISTRY_ADDRESS | string | `"0xc15d5a57a8eb0e1dcbe5d88b8f9a82017e5cc4af"` |  |
| clientgateway.scheduler.enabled | bool | `false` |  |
| clientgateway.scheduler.image.pullPolicy | string | `"IfNotPresent"` |  |
| clientgateway.scheduler.image.repository | string | `"aemocontainerregistry.azurecr.io/ddhub-client-gateway-scheduler"` |  |
| clientgateway.scheduler.image.tag | string | `"canary"` |  |
| clientgateway.scheduler.podAnnotations | object | `{}` |  |
| clientgateway.scheduler.probes.liveness | bool | `true` |  |
| clientgateway.scheduler.probes.readiness | bool | `true` |  |
| clientgateway.scheduler.resources | object | `{}` |  |
| ddhub-client-gateway-ui.enabled | bool | `false` |  |
| existingClaim.claimName | string | `"my-claim"` |  |
| existingClaim.enabled | bool | `false` |  |
| existingClaim.mountPath | string | `"/mnt/claim"` |  |
| fullnameOverride | string | `"ddhub-client-gateway"` |  |
| image.pullPolicy | string | `"IfNotPresent"` |  |
| image.repository | string | `"aemocontainerregistry.azurecr.io/ddhub-client-gateway-backend"` |  |
| image.tag | string | `"canary"` |  |
| imagePullSecrets | list | `[]` |  |
| ingress.annotations."appgw.ingress.kubernetes.io/ssl-redirect" | string | `"true"` |  |
| ingress.annotations."kubernetes.io/ingress.class" | string | `"azure/application-gateway"` |  |
| ingress.enabled | bool | `false` |  |
| ingress.hosts[0].host | string | `"ddhub-gateway-api-dev.energyweb.org"` |  |
| ingress.hosts[0].paths[0].backend.serviceName | string | `"ddhub-client-gateway-api"` |  |
| ingress.hosts[0].paths[0].backend.servicePort | int | `80` |  |
| ingress.hosts[0].paths[0].path | string | `"/*"` |  |
| ingress.hosts[0].paths[0].pathType | string | `"Prefix"` |  |
| ingress.tls[0].hosts[0] | string | `"ddhub-gateway-api-dev.energyweb.org"` |  |
| ingress.tls[0].secretName | string | `"dsb-tls-secret"` |  |
| nameOverride | string | `"ddhub-client-gateway"` |  |
| nodeSelector | object | `{}` |  |
| podAnnotations | object | `{}` |  |
| podSecurityContext | object | `{}` |  |
| probes.liveness | bool | `true` |  |
| probes.readiness | bool | `true` |  |
| pvc.accessMode | string | `"ReadWriteOnce"` |  |
| pvc.capacity | string | `"1Gi"` |  |
| pvc.enabled | bool | `false` |  |
| pvc.mountPath | string | `"/mnt/azure"` |  |
| pvc.storageClassName | string | `"default"` |  |
| replicaCount | int | `1` |  |
| resources | object | `{}` |  |
| securityContext | object | `{}` |  |
| service.port | int | `80` |  |
| service.type | string | `"ClusterIP"` |  |
| serviceAccount.annotations | object | `{}` |  |
| serviceAccount.create | bool | `true` |  |
| serviceAccount.name | string | `""` |  |
| tolerations | list | `[]` |  |

----------------------------------------------
Autogenerated from chart metadata using [helm-docs v1.5.0](https://github.com/norwoodj/helm-docs/releases/v1.5.0)
