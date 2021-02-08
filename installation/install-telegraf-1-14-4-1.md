## Telegraf 1.14.4.1Installation Manual 

##### Component 

- RedHat 7
- telegraf-1.14.4-1.x86_64.rpm

assume rpm-packages.tar.gz is under path : /Source/
______________________________________________________________________________________


//// To be monitored (VM) //// [user: root]
______________________________________________________________________________________

### Install package
```
yum install -y --cacheonly --disablerepo=* /Source/telegraf-1.14.4-1.x86_64.rpm
```



### Configurations (RESOURCE UTILIZE and POSTGRESQL)
```
vi /etc/telegraf/telegraf.conf

interval = "60s"

flush_interval = "60s"

#specify log path
   logfile = "/var/log/telegraf/telegraf.log"

#specify output
   urls = ["http://<influx_ip>:8086"]
   database = "telegraf"

#add input plugins (resource utilize) by uncommenting the following lines
[[inputs.netstat]]
[[inputs.net]]

#add input plugins (postgresql) by adding the following lines
[[inputs.postgresql]]
  address = "host=127.0.0.1 dbname=postgres user=extraw password=extraw port=5433 sslmode=disable"

[[inputs.postgresql]]
  address = "host=127.0.0.1 dbname=postgres user=extready password=extready port=5434 sslmode=disable"
```

### Start service
```
systemctl start telegraf
systemctl enable telegraf
```
