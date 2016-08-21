# shinken-pack-collectd-mdadm

## Description

This Shinken monitoring pack is used to manage mdadm services with our
standard deployment of Collectd.

We request Collectd data using unixsock plugin and collectd-nagios script from
collecd-utils package.

This pack depends to shinken-pack-collectd-base to work

## Objects

### Templates

#### Host templates

* collectd-mdadm: Manage all default thresholds and values for services

### Services

| Service name                | Description                     | Value specification         | DS        | Consolidation | Warning variable | Critical variable | Duplicate_foreach variable |
|-----------------------------|---------------------------------|-----------------------------|-----------|---------------|------------------|-------------------|----------------------------|
| Mdadm - $KEY$ active disks  | Check RAID device active disks  | $VALUE1$/md_disks-active    | value     | none          | $VALUE2$         | $VALUE3$          | _mdadm_devices             |
| Mdadm - $KEY$ failed disks  | Check RAID device failed disks  | $VALUE1$/md_disks-failed    | value     | none          | $VALUE4$         | $VALUE5$          | _mdadm_devices             |
| Mdadm - $KEY$ missing disks | Check RAID device missing disks | $VALUE1$/md_disks-missing   | value     | none          | $VALUE6$         | $VALUE7$          | _mdadm_devices             |
| Mdadm - $KEY$ spare disks   | Check RAID device spare disks   | $VALUE1$/md_disks-spare     | value     | none          | $VALUE8$         | $VALUE9$          | _mdadm_devices             |
| Mdadm - $KEY$ processes     | Check mdadm processes           | processes-$VALUE1$/ps_count | processes | none          | $VALUE2$         | $VALUE3$          | _mdadm_processes           |

## Default values

    _mdadm_devices      md0 $(md-0)$(2:2)$$(2:2)$$(0)$$(0)$$(0)$$(0)$$(0)$$(0)$
    _mdadm_processes    mdadm $(mdadm)$$(1:1)$$(1:1)$,md0_raid1 $(md0_raid1)$$(1:1)$$(1:1)$
