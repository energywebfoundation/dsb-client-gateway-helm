# dsb-client-gateway

![Version: 1.2.1](https://img.shields.io/badge/Version-1.2.1-informational?style=flat-square) ![Type: application](https://img.shields.io/badge/Type-application-informational?style=flat-square) ![AppVersion: 0.4.0](https://img.shields.io/badge/AppVersion-0.4.0-informational?style=flat-square)

A Helm chart for Kubernetes
## Introduction
This is a repository with helm chart for DSB Client Gateway application.

For more information about DSB Client Gateway please check the [repository](https://github.com/energywebfoundation/dsb-client-gateway).

## Quickstart

```
minikube start

helm install dsb-client-demo https://github.com/energywebfoundation/dsb-client-gateway-helm/archive/refs/tags/v1.1.2.tar.gz

kubectl get pods
```

## Values

| Key | Type | Default | Description |
|-----|------|---------|-------------|
| affinity | object | `{}` |  |
| autoscaling.enabled | bool | `false` |  |
| autoscaling.maxReplicas | int | `100` |  |
| autoscaling.minReplicas | int | `1` |  |
| autoscaling.targetCPUUtilizationPercentage | int | `80` |  |
| clientgateway.config.basic_auth_enabled | bool | `false` | Enable basic auth. (Once enabled, associated secret is required, eg: "dsb-client-gateway-secret") |
| clientgateway.config.cache_server_url | string | `"https://identitycache-staging.energyweb.org/v1"` | Sets the Energy Web IAM cache server URL, used to cache identities (as it can be expensive to rely only on querying smart contract data). |
| clientgateway.config.chain_id | int | `73799` | Sets the chain ID of the blockchain network. Options: 73799 (Volta), 246 (EWC) |
| clientgateway.config.dsb_base_url | string | `"https://dsb-demo.energyweb.org"` | The URL of the DSB Message Broker you want to connect to. Trailing / allowed. |
| clientgateway.config.event_server_url | string | `"https://identitycache-staging.energyweb.org/"` | Sets the Energy Web IAM events server URL, used to receive notification of approved DSB role claims. |
| clientgateway.config.events_emit_mode | string | `"BULK"` | Defines the format for messages pushed over a real-time communication channel. If bulk mode is chosen, messages will be sent as an array. At every 1 second interval, the gateway will emit an array of the latest messages received. If single mode is chosen, messages will be sent individually. Options: BULK, SINGLE |
| clientgateway.config.events_max_per_second | int | `100` | Defines how many events should be pushed per second, regardless of mode chosen (see above). |
| clientgateway.config.in_memory_db_filename | string | `"in-memory.json"` | Sets the filename of the JSON file the DSB Client Gateway will write to. The file will be written to the current working directory (subject to change). |
| clientgateway.config.parent_namespace | string | `"dsb.apps.energyweb.iam.ewc"` | Sets the Energy Web IAM application namespace. DSB related roles, such as user and messagebroker should fall under this namespace. |
| clientgateway.config.port | int | `3000` | Define the port the gateway will run on. |
| clientgateway.config.rpc_url | string | `"https://volta-rpc.energyweb.org/"` | Sets the blockchain RPC node to connect to retreive state from and submit transactions to. Should match the network given in CHAIN_ID. |
| clientgateway.config.websocket | string | `"NONE"` | Select WebSocket mode depending on architecture (i.e. preference for inbound or outbound connections). By default, the gateway will run a WebSocket server on /events. However, it can also operate as a client with additional configuration (see below). Alternatively, this functionality can be turned off. Options: SERVER, CLIENT, NONE |
| clientgateway.config.websocket_protocol | string | `""` | Sets the protocol the WebSocket client should request access to. Acceptable protocols are defined by the WebSocket server, however, this can also be left undefined. Note that if WEBSOCKET is set to SERVER this variable is ignored. The server will only accept connection requests on the dsb-messages protocol. |
| clientgateway.config.websocket_reconnect | bool | `false` | Define whether the WebSocket client should reconnect on connection error/close. |
| clientgateway.config.websocket_reconnect_max_retries | int | `10` | Define how many times the WebSocket client should attempt reconnection with the server upon receving connection error/close. |
| clientgateway.config.websocket_reconnect_timeout | int | `10000` | Define the interval between receiving a connection error/close and attempting to reconnect, in milliseconds. |
| clientgateway.config.websocket_url | string | `""` | Sets the URL of the WebSocket server the client should try to connect to. Required if WEBSOCKET is set to CLIENT. |
| existingClaim.claimName | string | `"my-claim"` |  |
| existingClaim.enabled | bool | `false` |  |
| existingClaim.mountPath | string | `"/mnt/claim"` |  |
| fullnameOverride | string | `"dsb-client-gateway"` |  |
| image.pullPolicy | string | `"IfNotPresent"` |  |
| image.repository | string | `"aemocontainerregistry.azurecr.io/dsb/client-gateway"` |  |
| image.tag | string | `"canary"` |  |
| imagePullSecrets | list | `[]` |  |
| ingress.annotations."alb.ingress.kubernetes.io/scheme" | string | `"internet-facing"` |  |
| ingress.annotations."kubernetes.io/ingress.class" | string | `"alb"` |  |
| ingress.enabled | bool | `false` |  |
| ingress.hosts[0].host | string | `"dsb-gateway-dev.energyweb.org"` |  |
| ingress.hosts[0].paths[0].backend.serviceName | string | `"client-gateway"` |  |
| ingress.hosts[0].paths[0].backend.servicePort | int | `80` |  |
| ingress.hosts[0].paths[0].path | string | `"/*"` |  |
| ingress.tls | list | `[]` |  |
| nameOverride | string | `"dsb-client-gateway"` |  |
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
