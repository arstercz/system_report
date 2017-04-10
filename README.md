# system_report
Wrap pt-stalk to collect forensic data about MySQL when problems occur

## how to use

The `run-pt-stalk` wrap the pt-stalk script, run with:
```
git clone https://github.com/chenzhe07/system_report.git
cd system_report
./run-pt-stalk interface mysql_port
```

## how to send mail when problems occur

Everyone can change for following code in pt-stalk script to send mail:
```
1319             echo "$msg on $(hostname)" \
1320             | mail -r 'report@system.com' -S smtp='127.0.0.1' -s "Collect triggered on $(hostname)" \
1321               "$OPT_NOTIFY_BY_EMAIL"
```

pt-stalk use `mail` command, we can change the sender and smtp server by 
`-r` and `-S` options.

## plugin

pt-stalk support the plugin so that we can change the problems occur's
conditions. Example in the plugin dirs is to summary the cpu by the
all MySQL process used.

all self-defined function should be named `trg_plugin`.


## pt-stalk

We had fixed the following bugs:

  [#1557877](https://bugs.launchpad.net/percona-toolkit/+bug/1557877)
  [#1644694](https://bugs.launchpad.net/percona-toolkit/+bug/1644694)
  [#976179](https://bugs.launchpad.net/percona-toolkit/+bug/976179)
  [#1083488](https://bugs.launchpad.net/percona-toolkit/+bug/1083488)

and add the following features:
```
1. capture traffic by use tcpdump;
2. output numa information;
```
