# zigbee2mqtt

![Version: 2.5.1](https://img.shields.io/badge/Version-2.5.1-informational?style=flat-square) ![AppVersion: 2.5.1](https://img.shields.io/badge/AppVersion-2.5.1-informational?style=flat-square)

Bridges events and allows you to control your Zigbee devices via MQTT

**Homepage:** <https://github.com/Koenkk/zigbee2mqtt>

## Maintainers

| Name | Email | Url |
| ---- | ------ | --- |
| Koen Kanters |  |  |

## Source Code

* <https://github.com/Koenkk/zigbee2mqtt-chart>

## Requirements

Kubernetes: `>=1.26.0-0`

## Values

| Key | Type | Default | Description |
|-----|------|---------|-------------|
| configmap.annotations | object | `{}` | annotations for the configmap created |
| customLabels | object | `{}` |  |
| extraResources | list | `[]` | Extra Resources. Define some extra resources to be created, such as ExternalResource or Secrets, etc. |
| fullnameOverride | string | `nil` | override the name of the objects generated |
| image.imagePullSecrets | object | `{}` | Container additional secrets to pull image |
| image.pullPolicy | string | `"IfNotPresent"` | Container pull policy |
| image.repository | string | `"koenkk/zigbee2mqtt"` | Image repository for the `zigbee2mqtt` container. |
| image.tag | string | `nil` | Version for the `zigbee2mqtt` container. If left as null it will use the chart appVersion |
| ingress | object | `{"annotations":{},"enabled":false,"hosts":[{"host":"chart-example.local","paths":[{"path":"/","pathType":"ImplementationSpecific"},{"path":"/api","pathType":"ImplementationSpecific"}]}],"ingressClassName":"contour","labels":{},"pathType":"Prefix","tls":[{"hosts":["yourdomain.com"],"secretName":"some-tls-secret"}]}` | Ingress configuration. Zigbee2mqtt does use webssockets, which is not part of the Ingress standart settings. most of the popular ingresses supports them through annotations. Please check https://www.zigbee2mqtt.io/guide/installation/08_kubernetes.html for examples. |
| ingress.enabled | bool | `false` | When enabled a new Ingress will be created |
| ingress.hosts | list | `[{"host":"chart-example.local","paths":[{"path":"/","pathType":"ImplementationSpecific"},{"path":"/api","pathType":"ImplementationSpecific"}]}]` | list of hosts that should be allowed for the zigbee2mqtt service |
| ingress.ingressClassName | string | `"contour"` | The ingress class name for the ingress |
| ingress.labels | object | `{}` | Additional labels for the ingres |
| ingress.pathType | string | `"Prefix"` | Ingress implementation specific (potentially) for most use cases Prefix should be ok |
| ingress.tls | list | `[{"hosts":["yourdomain.com"],"secretName":"some-tls-secret"}]` | configuration for tls service (ig any) |
| nameOverride | string | `nil` | override the release name |
| secretesMigratorContainer | object | `{"imagePullSecrets":{},"pullPolicy":"IfNotPresent","repository":"mikefarah/yq","securityContext":{"runAsUser":0},"tag":"4.45.1"}` | details about the image |
| secretesMigratorContainer.imagePullSecrets | object | `{}` | Container additional secrets to pull image |
| secretesMigratorContainer.pullPolicy | string | `"IfNotPresent"` | Container pull policy |
| secretesMigratorContainer.repository | string | `"mikefarah/yq"` | Image repository for the `zigbee2mqtt` container. |
| secretesMigratorContainer.securityContext | object | `{"runAsUser":0}` | permissions to create files since z2m runs with root (by default) |
| secretesMigratorContainer.tag | string | `"4.45.1"` | Version for the `zigbee2mqtt` container. |
| service.annotations | object | `{}` | annotations for the service created |
| service.port | int | `8080` | port in which the service will be listening |
| service.type | string | `"LoadBalancer"` | type of Service to be created |
| statefulset.affinity | object | `{}` | Node affinity for the pods |
| statefulset.annotations | object | `{}` | annotations for the statefulset created |
| statefulset.command | object | `{}` | Overrides the entrypoint of the container |
| statefulset.dnsPolicy | string | `"ClusterFirst"` | pod dns policy |
| statefulset.lifecycle | object | `{}` | Lifecycle configuration for the container |
| statefulset.livenessProbe | object | `{"failureThreshold":5,"httpGet":{"path":"/","port":"web"},"initialDelaySeconds":60,"periodSeconds":30,"timeoutSeconds":10}` | Configures Container liveness probe |
| statefulset.nodeSelector | object | `{}` | Select specific kube node, this will allow enforcing zigbee2mqtt running only on the node with the USB adapter connected |
| statefulset.podAnnotations | object | `{}` | annotations for the pod template |
| statefulset.podSecurityContext | object | `{"seccompProfile":{"type":"RuntimeDefault"}}` | Configure Pods Security Context |
| statefulset.resources | object | `{"limits":{"cpu":"200m","memory":"600Mi"},"requests":{"cpu":"200m","memory":"600Mi"}}` | CPU/Memory configuration for the pods |
| statefulset.secrets.name | string | `""` | the name for the kubernets secret to mount as secret.yaml. This can be referenced in the config by using advanced configurations https://www.zigbee2mqtt.io/guide/configuration/frontend.html#advanced-configuration |
| statefulset.securityContext | object | `{"capabilities":{"add":["SYS_ADMIN"]},"privileged":true}` | Configure Container Security Context |
| statefulset.storage.annotations | object | `{}` | annotations to add to the persistent volume claim |
| statefulset.storage.enabled | bool | `false` |  |
| statefulset.storage.existingVolume | string | `""` |  |
| statefulset.storage.matchExpressions | object | `{}` |  |
| statefulset.storage.matchLabels | object | `{}` |  |
| statefulset.storage.size | string | `"1Gi"` |  |
| statefulset.storage.storageClassName | string | `"freenas-nfs-csi"` | the name for the storage class to be used in the persistent volume claim |
| statefulset.tolerations | object | `{}` | Node taint tolerations for the pods |
| statefulset.volumeMounts | list | `[]` | Additional volumeMounts to the server main container |
| statefulset.volumes | list | `[]` | Additional volumes to the server pod |
| zigbee2mqtt.advanced.adapter_concurrent | string | `nil` | Optional: configure adapter concurrency (e.g. 2 for CC2531 or 16 for CC26X2R1) (default: null, uses recommended value) |
| zigbee2mqtt.advanced.adapter_delay | int | `0` | Optional: Set the adapter delay, only used for Conbee/Raspbee adapters (default 0). In case you are having issues try `200`. For more information see https://github.com/Koenkk/zigbee2mqtt/issues/4884 |
| zigbee2mqtt.advanced.cache_state | bool | `true` | Has to be true when integrating via Home Assistant (default: true) |
| zigbee2mqtt.advanced.cache_state_persistent | bool | `true` | Optional: persist cached state, only used when cache_state: true (default: true) |
| zigbee2mqtt.advanced.cache_state_send_on_startup | bool | `true` | Optional: send cached state on startup, only used when cache_state_persistent: true (default: true) |
| zigbee2mqtt.advanced.channel | int | `11` | Optional: ZigBee channel, changing requires re-pairing of all devices. (Note: use a ZLL channel: 11, 15, 20, or 25 to avoid Problems) (default: 11) |
| zigbee2mqtt.advanced.elapsed | bool | `false` | Optional: Add an elapsed attribute to MQTT messages, contains milliseconds since the previous msg (default: false) |
| zigbee2mqtt.advanced.last_seen | string | `"disable"` | Optional: Add a last_seen attribute to MQTT messages, contains date/time of last Zigbee message possible values are: disable (default), ISO_8601, ISO_8601_local, epoch (default: disable) |
| zigbee2mqtt.advanced.legacy_api | bool | `false` | Optional: disables the legacy api (default: shown below) |
| zigbee2mqtt.advanced.log_level | string | `"info"` |  |
| zigbee2mqtt.advanced.log_output | list | `["console"]` | Optional: network encryption key GENERATE will make Zigbee2MQTT generate a new network key on next startup Note: changing requires repairing of all devices (default: shown below) network_key: null |
| zigbee2mqtt.advanced.report | bool | `true` | Optional: Enables report feature, this feature is DEPRECATED since reporting is now setup by default when binding devices. Docs can still be found here: https://github.com/Koenkk/zigbee2mqtt.io/blob/master/docs/information/report.md |
| zigbee2mqtt.advanced.timestamp_format | string | `"YYYY-MM-DD HH:mm:ss"` |  |
| zigbee2mqtt.advanced.transmit_power | int | `5` | Optional: Transmit power setting in dBm (default: 5). This will set the transmit power for devices that bring an inbuilt amplifier. It can't go over the maximum of the respective hardware and might be limited by firmware (for example to migrate heat, or by using an unsupported firmware). For the CC2652R(B) this is 5 dBm, CC2652P/CC1352P-2 20 dBm. |
| zigbee2mqtt.availability.active.timeout | int | `10` | Time after which an active device will be marked as offline in minutes (default = 10 minutes) |
| zigbee2mqtt.availability.passive.timeout | int | `1500` | Time after which a passive device will be marked as offline in minutes (default = 1500 minutes aka 25 hours) |
| zigbee2mqtt.blocklist | list | `[]` | Locking devices from the network ( ieeeAddr ) |
| zigbee2mqtt.external_converters | list | `[]` |  |
| zigbee2mqtt.frontend.auth_token | string | `nil` | Optional, enables authentication, disabled by default, cleartext (no hashing required) |
| zigbee2mqtt.frontend.enabled | bool | `true` | If the front end should be enabled, true by default. Pod health checks are based on this, so disabling it will cause an error loop unless health checks are updated. |
| zigbee2mqtt.frontend.host | string | `""` | Optional, empty by default to listen on both IPv4 and IPv6. Opens a unix socket when given a path instead of an address (e.g. '/run/zigbee2mqtt/zigbee2mqtt.sock') Don't set this if you use Docker or the Home Assistant add-on unless you're sure the chosen IP is available inside the container |
| zigbee2mqtt.frontend.port | int | `8080` | Mandatory, default 8080 |
| zigbee2mqtt.frontend.url | string | `nil` | Optional, url on which the frontend can be reached, currently only used for the Home Assistant device configuration page |
| zigbee2mqtt.homeassistant.discovery_topic | string | `"homeassistant"` |  |
| zigbee2mqtt.homeassistant.enabled | bool | `true` |  |
| zigbee2mqtt.homeassistant.legacy_entity_attributes | bool | `true` |  |
| zigbee2mqtt.homeassistant.legacy_triggers | bool | `false` |  |
| zigbee2mqtt.homeassistant.status_topic | string | `"hass/status"` |  |
| zigbee2mqtt.mqtt.server | string | `"mqtt://localhost:1883"` | Required: MQTT server URL (use mqtts:// for SSL/TLS connection) |
| zigbee2mqtt.ota | object | `{"disable_automatic_update_check":false,"ikea_ota_use_test_url":false,"update_check_interval":1440}` | Optional: OTA update settings See https://www.zigbee2mqtt.io/guide/usage/ota_updates.html for more info |
| zigbee2mqtt.ota.disable_automatic_update_check | bool | `false` | Disable automatic update checks |
| zigbee2mqtt.ota.ikea_ota_use_test_url | bool | `false` | Optional: use IKEA TRADFRI OTA test server, see OTA updates documentation (default: false) |
| zigbee2mqtt.ota.update_check_interval | int | `1440` | Minimum time between OTA update checks |
| zigbee2mqtt.permit_join | bool | `false` | Optional: allow new devices to join. |
| zigbee2mqtt.serial.baudrate | int | `115200` | Optional: Baud rate speed for serial port, this can be anything firmware support but default is 115200 for Z-Stack and EZSP, 38400 for Deconz, however note that some EZSP firmware need 57600. |
| zigbee2mqtt.serial.disable_led | bool | `false` | Optional: disable LED of the adapter if supported (default: false) |
| zigbee2mqtt.serial.port | string | `"/dev/ttyACM0"` | Required: location of the adapter (e.g. CC2531). USB adapters - use format "port: /dev/ttyACM0" To autodetect the USB port, set 'port: null'. Ethernet adapters - use format "port: tcp://192.168.1.12:6638" |
| zigbee2mqtt.serial.rtscts | bool | `false` | Optional: RTS / CTS Hardware Flow Control for serial port (default: false) |
| zigbee2mqtt.timezone | string | `"UTC"` |  |

