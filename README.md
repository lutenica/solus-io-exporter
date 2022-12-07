# Solus IO (SolusVM 2.0) prometheus exporter

## General info:

 This is not an exporter per se, though it may become one some day. For now it is a script that is intended to obtain some basic info from Solus IO and plugs into node-exporter's textfile collector. It means you don't need to open up additional privileges and ports just for this information, rather, it  plugs into existing tooling from node-exporter.

It comes prepared to build for .deb packages, though if you want you can do a
rpm based build.

## Data collected:

- Compute resources
- Servers
- Pending tasks
- Failed tasks
- Upgrades pending or not

All of this is collected as gauges, where upgrades pending is 1 for yes, 0 for no.

## Installation

 You can either directly clone the files from the repository and build as a debian package. All files required for dpkg-buildpackage are present.
Alternatively you can also simply place the script from /src/ into a directory of your choosing as well as the conf/config file. The script will default to /etc/default/sio-exporter for the config file, or you can provide a path via an argument like so:

```
/path/to/sio-exporter -c /path/to/config
```
or
```
/path/to/sio-exporter --config /path/to/config
```

Details for the config file can be found in the example in the repo.

To actually start getting data you need to run the script with the frequency desired either through cron or a systemd-timer. 

All that is left now is to configure node-exporter's --collector.textfile and --collector.textfile.directory parameters. The former enables that function (Which is on by default) and the latter let's you specify the directory where it will read the file from. This needs to match the path to the file you've specified in the sio-exporter config file.


## Future plans / extensions

 This can easily be extended to collect even more data from SolusVM, for now this is what I need.  I am open to suggestions though :).
