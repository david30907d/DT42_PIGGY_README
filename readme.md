# DT42 Piggy Readme

If somethings goes wrong, please check the README of these repo.

* Front-end: <https://github.com/david30907d/DT42_PIGGY_WEB>
* Piggy-kafka: <https://github.com/david30907d/dt42-piggy-kafka>
* API: <https://github.com/david30907d/DT42_PIGGY_API>

## Install

1. Front-end: `docker pull davidtnfsh/dt42_piggy_front_end:latest`
2. Kafka cluster: `git clone; git submodule update --init`
3. API: `docker pull davidtnfsh/dt42_piggy_api:latest`

## Run

> Caveat: Please invoke these commands in order!

1. Fron-end: `docker run --rm -p 5000:5000 -it davidtnfsh/dt42_piggy_front_end:latest`
2. Kafka cluster: `cd /<path>/dt42-piggy-kafka; docker-compose up`
3. API: `cd /<path>/DT42_PIGGY_API; docker-compose up`
    * Because DT42 trainer.pipelines still have some issue, so use `cd /<path>/DT42_PIGGY_API; docker-compose -f docker-compose.test.yml up` just for now.
4. Dashboard: `docker run -itd -p 3000:3000 --name metabase metabase/metabase:v0.36.6`

## Init Database

```bash
docker-compose exec -T postgres sh -c 'psql -U postgres -f /tmp/stored_procedures.sql'
docker-compose exec -T postgres sh -c 'psql -U postgres -f /tmp/init.sql'
```

## Create User to Login

<https://github.com/david30907d/DT42_PIGGY_API#run>