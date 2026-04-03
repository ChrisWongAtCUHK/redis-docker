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
docker exec -it redis redis-cli -u redis://default:${REDIS_HOST}:${REDIS_PORT}
```

## Connect and print the raw output
```
docker exec -it redis redis-cli --raw
```

## List all keys
```
127.0.0.1:6379> KEYS *
```

