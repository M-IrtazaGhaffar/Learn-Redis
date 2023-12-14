# Learn-Redis

## Install redis/redis-stack-server in Docker
```
docker run -d --name redis-stack-server -p 6379:6379 redis/redis-stack-server:latest
```

## Install redis/redis-stack in Docker
```
docker run -d --name redis-stack -p 6379:6379 -p 8001:8001 redis/redis-stack:latest
```

## Now Run Redis after running the Docker
```
redis-cli
```

## Setting a value in the Redis
```
set name irtaza
```
```
set name:1 irtaza
set name:2 abdullah
```

## Getting the value from Redis
```
get name:1
get name:2
```

## Settiig a value if the Key don't exist
```
set name:4 usama nx
```
Redis will respond with OK but if we use
```
set name:1 IRTAZA nx
```
then Redis will respond with some error (Nil)

## Getting more then one values from Redis
```
mget name:1 name:2 university:3
```
