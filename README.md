### - Dexcom

Create an environment script with relevent values as showsn below

```bash
#!/bin/bash

BROKER_URL="pkc-xxx.region.gcp.confluent.cloud:9092"
API_KEY="LLLLLLLLLLLLLLLLLL"
API_SECRET="BBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBB"
IP=0.0.0.0

export MY_PUBLIC_IP=${IP}
export BOOTSTRAP_SERVERS="${BROKER_URL}"
export SASL_JAAS_CONFIG="org.apache.kafka.common.security.plain.PlainLoginModule required username\=\"${API_KEY}\" password\=\"${API_SECRET}\";"
export SR_BOOTSTRAP_SERVERS="SASL_SSL://${BROKER_URL}"
export KEYSTORE_PASS=changeit

export CCLOUD_BROKER_URL=${BROKER_URL}
export CCLOUD_API_KEY=${API_KEY}
export CCLOUD_API_SECRET=${API_SECRET}
```

```bash
# edit setenv-la.sh or  eu
. ./setenv-la.sh 
#create config
cp ./template/docker-compose.yml  docker-compose.yaml

docker-compose up -d
```

