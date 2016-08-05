# Monitoring
Monitoring consists of following components:

* Ganglia - for metrics collection which are then shipped into graphite
* rsyslog - for log collection which are shipped to logstash and then accsesible
trought kibana

## Ganglia

Client side glaglia daemon is gmond

### Mandatory variables

* ganglia_cluster_port_number - ip of the master server
* ganglia_master_ip - ganglia port number
* ganglia_cluster_name - ganglia
* ganglia_master_name - shostname/ip of the master server

## rsyslog

The syslog daemon recieves all logs and sends them to central server.  
The hosts key and certificate are generated on the CA(locally).

### Mandtory variables

* rsyslog_collector - server to which logs are shipped
* rsyslog_collector_port - syslog port
* syslog_certs_path - directory for ssl certificates
* syslog_tls_ca - ca crt file location
* syslog_tls_cert - location of the host's certificate
* syslog_tly_key - location of the hosts ke file
* syslog_permited_peers: This variable must be set on the senders. This is the name of the log collector as written in the collectors certificate CN.
* syslog_permited_senders: This variable must be set on the collector. It contains a list of all names of senders as written in their certificate CN.
* monitoring_syslog_ca_files: Path to the local directory where ssl keys, certs are stored.

### Optional variables

* hive_role - set this to master (ONLY)on the collector server.
* rsyslog_queue_size: Size of the rsyslog queue
* rsyslog_low_watermark: Queue size at which the queue stops being written to the disk, and is written to the RAM instead
* rsyslog_high_watermark: Queue size at which queue is written to the disk
* rsyslog_discard_watermark: Queue size at which to start discarding lower prioriy logs.
