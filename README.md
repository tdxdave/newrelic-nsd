# newrelic-nsd
Newrelic Driver for AOLserver

You need the Newrelic SDK to begin with. 


To compile:
I forgot exactly the command line I used. You need to point it to the relevant AOLserver, Tcl and the Newrelic agent libraries to get it to compile. I'll see if I can find my notes.

To install:

Copy newrelic_common_wrap.so, newrelic_common_wrap.tcl pkgIndex.tcl to a directory 
newrelic_common_wrap_0.1 under a directory on the Tcl Library path.

Add the following to the AOLserver config file:
# newrelic config                                                                                   
ns_section "ns/server/${server}/newrelic"
ns_param key "NEWRELIC_KEY"
ns_param app_name "APP_NAME"

Add the following to a Tcl file that runs on AOLserver startup:

 package require newrelic_common_wrap
 newrelic_register_message_handler ""
 set app_name [ns_config "ns/server/[ns_info server]/newrelic" app_name ""]
 set key [ns_config "ns/server/[ns_info server]/newrelic" key ""]
 newrelic_init  $key $app_name Tcl 8.5
 ns_log notice "New Relic Initialized newrelic_init  $key $app_name Tcl 8.5"

See newrelic-openacs for examples for setting up filters to report to Newrelic.
