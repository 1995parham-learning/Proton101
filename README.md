# Proton101

## Introduction

[Proton](https://github.com/timeplus-io/proton) is a streaming SQL processor developed by the ClickHouse team and written in C++.
It is designed to be easier and faster than Apache Flink. I plan to test it out here,
initially using its client, and later by writing some code.

## Using Proton Client

First, run the docker compose:

```bash
docker compose up
```

Then, attach into it:

```bash
docker exec -ti proton101-proton-1 bash

proton-client
```

and create a random stream using its client:

```sql
CREATE RANDOM STREAM devices(
                  device string default 'device'||to_string(rand()%4),
                  temperature float default rand()%1000/10)
```

you can query the realtime data as follows:

```sql
SELECT device, count(*), min(temperature), max(temperature)
FROM devices GROUP BY device
```
