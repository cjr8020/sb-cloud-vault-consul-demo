# sb-cloud-vault-consul-demo

## Consul backend

Spring Cloud Vault can obtain credentials for Consul.
The Consul integration requires 

```
		<dependency>
			<groupId>org.springframework.cloud</groupId>
			<artifactId>spring-cloud-vault-config-consul</artifactId>
		</dependency>
```

The integration can be enabled by setting
```
	spring.cloud.vault.consul.enabled=true  # default is "false"
	spring.cloud.vault.consul.role=<role-id>
```

for instance: 
```
spring.cloud.vault:
  authentication: APPROLE
  app-role.role-id: ${role-id}
  generic.enabled: false
  kv:
    enabled: true
  scheme: https
  consul:
    enabled: true
    role: ${spring.cloud.vault.application-name:${spring.application.name}}
```

`enabled`

"true" enables the Consul backend config usage
	
`role`

sets the role name of the Consul role definition

`backend`

sets the path of the Consul mount to use

`token-property`

sets the property name in which the Consul ACL token is stored
