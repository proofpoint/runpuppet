NAME
----

runpuppet

SYNOPSIS
--------

.. code:: shell

   /etc/runpuppet [options] [puppet-options] [class [...]]
      --verbose            Produce verbose output
      --lockfile=_file_    Use _file_ as lockfile 
      --progress           Show puppet's output (default if on TTY)
      --agent              Run puppet as agent (not standalone)
      --noop               Do a puppet dry-run
      --noupdate-inventory Don't update CMDB
      --debug              Produce debugging output (from puppet as well)
      --trafficcontrol     Pass trafficcontrol parameters for posting to CMDB

      Puppet Options:
         --color
         --enable
         --trace
         --fqdn
         --logdest
         --certname
         --server
         --ca_server
         --environment
         --report

DESCRIPTION
-----------

The **runpuppet** command runs puppet with a set of options, interprets its output, posts the results to CMDB and produces a message and exit value compatible with the Nagios API. It also does some pre-run and post-run cleanup that can cause problems for some versions of puppet. It enables [Puppet Reporting and Monitoring].

Lockfile
~~~~~~~~

If ``/etc/lock-puppet`` exists, it locks puppet from executing (runpuppet exits successfully with a Puppet Status of **skip**).

When ``/etc/lock-puppet`` is empty, it locks puppet "forever" (that is, until the file no longer exists). If the first line is an integer, it's taken as an epoch time at which the lock will expire (allowing you to write an automatically-expiring lockfile).

