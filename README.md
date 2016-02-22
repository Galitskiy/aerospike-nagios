#Note:

The previous implementation of the nagios plugin has been moved to the
`legacy` branch.


#Introduction

aerospike_nagios.py simplifies nagios configurations for Aerospike clusters.
The goal is to reduce the complexity to 2 simple steps.

1. Copy aerospike_nagios.py to your Nagios server
2. Add aerospike configs into Nagios

#Features

- Can monitor any stat returned by
  - `$ asinfo -v 'statistics' [-h <HOST>]`
  - `$ asinfo -v 'namespace/<NAMESPACE NAME>' [-h host]`

###Known Issues

- Host based monitoring instead of cluster based monitoring

### Requirements
1. Aerospike python client. See (this page)[http://www.aerospike.com/docs/client/python/install/]

### Getting Started

1. Copy aerospike_nagios.py to your prefered scripts dir

    > Eg: /opt/aerospike/bin/

1. Add the nagios service definitions for aerospike_nagios.py

1. Add the aerospike service to host(s)

1. Restart/reload nagios


### Aerospike nagios Plugin

See *aerospike_nagios.py*, this is the file that nagios will schedule to perform
queries against Aerospike. Other than copying it to the appropriate location,
you are not required to interact with it.

###  Usage

    Usage:
     -h host (default 127.0.0.1)
     -p port (default 3000)
     -s "statistic" (Eg: "free-pct-memory")
     -n "namespace" (Eg: "namespace/test")

To monitor all general statistics:
`aerospike_nagios.py -h YOUR_ASD_HOST`

To monitor all statistics in a namespace:
`aerospike_nagios.py -h YOUR_ASD_HOST -n YOUR_NAMESPACE`

To monitor a specific general statistic:
`aerospike_nagios.py -h YOUR_ASD_HOST -s SERVICE_NAME`

To monitor a specific statistic in a namepsace:
`aerospike_nagios.py -h YOUR_ASD_HOST -s SERVICE_NAME -n YOUR_NAMESPACE`
