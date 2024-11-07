# Setup redis cluster locally
This is the minimum setup to run redis as a cluster locally

+++++++++++++++++++++++++++++++++++

DO NOT USE THIS IN PRODUCTION
DEVELOPMENT ONLY

+++++++++++++++++++++++++++++++++++

## 01 Install redis
Google it

## 02 Setup port
In each of the three files, edit the port number.
Also change the configuration file to match it.
eg:

```conf
# redis.conf file
port 8010
cluster-enabled yes
cluster-config-file nodes-8010.conf
cluster-node-timeout 5000
```

## 03 Start redis instance
Each on its own terminal

```bash
// In terminal 1
redis-server redis-1.conf
// In terminal 2
redis-server redis-2.conf
// In terminal 3
redis-server redis-3.conf
```

## 04 Configure cluster
In another terminal create the custer

```bash
redis-cli --cluster create 127.0.0.1:8010 127.0.0.1:8011 127.0.0.1:8012 --cluster-replicas 0
```
Confirm with `yes`

You will see the succes messsage:

```bash
[OK] All nodes agree about slots configuration.
>>> Check for open slots...
>>> Check slots coverage...
[OK] All 16384 slots covered.
```

#end
