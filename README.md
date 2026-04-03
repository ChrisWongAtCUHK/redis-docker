# Redis

## Redis quick start guide
### Install
```
docker run -d --name redis -p 6379:6379 -p 8001:8001 redis:latest
```
### Connect
```
docker exec -it redis redis-cli
```
[Redis Cloud](https://cloud.redis.io/#/databases/14166340/subscription/3199591/view-bdb/configuration)
```
docker exec -it redis redis-cli --no-auth-warning -u redis://default:${REDIS_PWD}@${REDIS_HOST}:${REDIS_PORT}
```
```
redis-12325.c10.us-east-1-2.ec2.cloud.redislabs.com:12325> TYPE "sample_restaurant:10"
redis-12325.c10.us-east-1-2.ec2.cloud.redislabs.com:12325> JSON.GET "sample_restaurant:10"
```
## Connect and print the raw output
```
docker exec -it redis redis-cli --raw
```

## List all keys
```
127.0.0.1:6379> KEYS *
```
```
redis-12325.c10.us-east-1-2.ec2.cloud.redislabs.com:12325> KEYS "sample_restaurant:*"
```

## Index
```
redis-12325.c10.us-east-1-2.ec2.cloud.redislabs.com:12325> FT._LIST
redis-12325.c10.us-east-1-2.ec2.cloud.redislabs.com:12325> FT.INFO idx:smpl_restaurant 
```

## Search data
```
redis-12325.c10.us-east-1-2.ec2.cloud.redislabs.com:12325>FT.SEARCH idx:smpl_restaurant "@name:Dragon Noodle"
```

## JSON.SET
```
127.0.0.1:6379>JSON.SET sample_restaurant:1 $ '{"name":"Trojan Feast","cuisine":"Mediterranean","location":"-98.5921,29.7265"}'
127.0.0.1:6379>FT.CREATE idx:smpl_restaurant ON JSON PREFIX 1 "sample_restaurant:" SCHEMA $.name AS name TEXT $.cuisine AS cuisine TEXT $.location AS location TEXT

```