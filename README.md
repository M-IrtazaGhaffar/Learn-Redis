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

## Setting more then one values in Redis
```
mset name:1 "IRTAZA" name:2 "ABDULLAH" university:3 "AHMED"
```

## Increment a value in Redis
```
set count 0
incr count
```

## Increment a value by 10 in Redis
```
set count 0
incrby count 10
```

## Using Redis with Node JS
```
const express = require('express')
const { client } = require('./client')
const app = express()
const port = 5000

app.get('/:name', async (req, res) => {
    console.log(req.params);
    const v1 = await client.get(`name:${req.params.name}`)
    await client.set('name:1', "IRTAZA")
    const v2 = await client.get(`name:${req.params.name}`)
    res.json({
        prev: v1,
        now: v2
    })
    await client.expire(`name:${req.params.name}`, 10)
})
app.listen(port, () => console.log(`Example app listening on port ${port}!`))
```

## Delete or Expire a key in Redis after 10 sec
```
expire name:1 10
```
