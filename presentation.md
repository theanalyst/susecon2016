# RADOSGW: Opening the Gateway for Administrators

## Abstract

RADOSGW (RGW from now on) is an HTTP gateway for storing objects in a Ceph cluster.
It speaks SWIFT (Open Stack) and S3 (Amazon), comes with an empbedded web server,
is highly customizable and is under active development.

Given it's high degree of customization, and that as far as Ceph components go,
it is still somewhat of the new kid, RGW may be a little daunting to deploy and
configure. We would like to focus this talk on the idea that if you put a little
into RGW, you will get a lot out.

In the hopes of clearly depicting the place of RGW in the Ceph ecosystem, we will
present the architecture of RGW, including frontend options, supported protocols
and touch on a bit of the inner workings of RGW. We will discuss some of most recent
developments in RGW, such as it's multi-site capability and static website feature.
Finally, we would like to dive deeply into deployment and configuration, demonstrating
how an administrator might: setup a basic gateway, architect their cluster to make use
of multi-site or federated gateways, and demonstrate some tips and tricks we've found
during our work with RGW.
