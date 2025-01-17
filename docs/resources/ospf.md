---
page_title: "panos: panos_ospf"
subcategory: "Network"
---

# panos_ospf

Manages OSPF config attached to a virtual router.


## Import Name

NGFW:

```shell
<virtual_router>
```

Panorama:

```shell
<template>::<virtual_router>
```


## Example Usage

```hcl
resource "panos_ospf" "example" {
    template = panos_panorama_template.x.name
    virtual_router = panos_panorama_virtual_router.x.name
    enable = true
    router_id = "10.5.7.9"
    enable_graceful_restart = true
    grace_period = 121
    helper_enable = true
    lsa_interval = 3
    max_neighbor_restart_time = 141
    spf_calculation_delay = 4
}

resource "panos_panorama_template" "x" {
    name = "my template"
}

resource "panos_panorama_virtual_router" "x" {
    template = panos_panorama_template.x.name
    name = "my virtual router"
}       
```


## Argument Reference

Panorama:

* `template` - (Optional, but Required for Panorama) The template location.

The following arguments are supported:

* `virtual_router` - (Required) The virtual router name.
* `enable` - (bool) Enable flag.
* `router_id` - Router ID.
* `reject_default_route` - (bool) Reject default route.
* `allow_redistribute_default_route` - (bool) Allow redistribute default route.
* `rfc_1583` - (bool) RFC 1583.
* `spf_calculation_delay` - (float) SPF calculation delay.
* `lsa_interval` - (float) LSA interval.
* `enable_graceful_restart` - (bool) Enable graceful restart.
* `grace_period` - (int) Grace period.
* `helper_enable` - (bool) Helper enable.
* `strict_lsa_checking` - (bool) Strict LSA checking.
* `max_neighbor_restart_time` - (int) Max neighbor restart time.
* `bfd_profile` - BFD profile name.
