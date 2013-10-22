runpuppet
=========

Puppet client execution wrapper

The runpuppet command invokes 'puppet agent' and reads its output, line by
line, interpreting its success or failure in a manner compatible with the
Nagios Plugin API. It also reports the results to a CMDB.
