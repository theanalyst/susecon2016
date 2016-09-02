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

## Presentation Outline/Draft

### Title
- RADOSGW: Opening the Gateway for Administrators

### Intro
- A few words about Abhishek and Karol

### Agenda
- General Ceph overview
- Where does RGW fit into the ecosystem
- RGW architecture
- Features (S3, Swift, static website)
- Basic installation and configuration
- Multisite

### Ceph Overview
- Open source
- Software defined storage
- Distributed
- No single point of failure
- Massively scalable
- Self healing
- Unified storage: object, block and file

### Ceph Arch - 1
- Slide presenting diagram of overall Cecph arch

        APP        HOST/VM       CLIENT
        /\           /\            /\
        ||           ||            ||
        \/           \/            \/
        RGW          RBD         CEPHFS
        -------------------------------
                   LIBRADOS
        -------------------------------
                    RADOS
        -------------------------------

### Ceph Arch - 2
- Slide touching on RADOS (Reliable Distributed Object Storage)

### Ceph Arch - 3
- Slide touching on LIBRADOS

### Ceph Arch - 4
- Slide touching on MONs and OSDs

### RADOS Gateway (RGW) Intro
- REST gateway to a Ceph Storage Cluster
- Supports S3, Swift
- Static Website

### RGW Arch
- Diagram showing basic RGW arch

             APP                   APP
             /\                    /\
             ||                    ||  <- REST
             \/                    \/
             RGW                   RGW
          LIBRADOS              LIBRADOS
             /\                    /\
             ||                    ||  <- Socket
             \/                    \/
        ---------------------------------
                   Ceph Cluster

        ---------------------------------

### RGW S3
- Touch on what S3 is
- Some S3 client options

### RGW Swift
- Touch on what Swift is
- Some Swift client options

### S3 vs Swift
- Mention key differences
- Pros/Cons

### RGW Static Website
- Touch on the static website feature and how it's useful

### Prerequisite to RGW Deployment
- Describe minimum cluster
- `ceph-deploy/SALT`

### Basic RGW Deployment - 1
- Live or record demo
- `ceph-deploy/SALT` RGW Installation

### Basic RGW Deployment - 2
- Highlight `/etc/ceph.conf`
- Turning up debugging
- Frontend choices
- SSL, ports

### Basic RGW Deployment - 3
- Showcase `radosgw-admin` command for:
  - user creation
  - subuser creation
  - secret keys

### Interlude - S3 test
- Show a quick:
  - S3 bucket create
  - S3 file upload
  - S3 file download

### Multisite RGW - 1
- Explain the move to multisite
- Federated vs Multisite

### Multisite RGW - 2
- Touch on how Multisite works
- Active - Active
- Background sync

### Multisite RGW Deployment - 1
- Building on existing cluster
- Add second cluster

### Multisite RGW Deployment - 2
- Configure using `radosgw-admin` and discuss:
  - Period
  - Realm
  - Zone Groups
  - Zones
- [Multsite doc](https://github.com/ceph/ceph/blob/master/doc/radosgw/multisite.rst)

### Interlude - Multisite S3 Test
- Verify users created in first S3 test have synced to second cluster
- Show a quick:
  - S3 bucket create
  - S3 file upload
  - S3 file download
- Verify sync
