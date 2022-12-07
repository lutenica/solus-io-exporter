# Solus IO (SolusVM 2.0) prometheus exporter

## General info:

 This is not an exporter per se, though it may become one some day.
For now it is a script that is intended to obtain some basic info from Solus IO and
plugs into node-exporter's textfile collector. You also need a cron/timer to
run as frequently as you need metrics exported.
 
 To that end you need to configure the --collector.textfile and --collector.textfile.directory options
in the node-exporter configuration. You can then use the configuration files to
specify the directory in question as well as your API key. sio_prom is an
example output file. 

 It comes prepared to build for .deb packages, though if you want you can do a
rpm based build.

## Data collected:

- Compute resources
- Servers
- Pending tasks
- Failed tasks
- Upgrades pending or not

All of this is collected as gauges, where upgrades pending is 1 for yes, 0 for no.

## Future plans / extensions

 This can easily be extended to collect even more data from SolusVM, for now this is what I need. 
I am open to suggestions.
