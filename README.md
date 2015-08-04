# newrelic-nsd
Newrelic Driver for AOLserver

To compile:

To install:

Copy newrelic_common_wrap.so, newrelic_common_wrap.tcl pkgIndex.tcl to a directory 
newrelic_common_wrap_0.1 under a directory on the Tcl Library path.

Add the following to the AOLserver config file:

Add the following to a Tcl file that runs on AOLserver startup:

 package require newrelic_common_wrap
 newrelic_register_message_handler ""
 set app_name [ns_config "ns/server/[ns_info server]/newrelic" app_name "SERVER"]
 set key [ns_config "ns/server/[ns_info server]/newrelic" key ""]
 newrelic_init  $key $app_name Tcl 8.5
 ns_log notice "New Relic Initialized newrelic_init  $key $app_name Tcl 8.5"
