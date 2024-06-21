![](docs/images/px4_septentrio_banner.png "PX4 Septentrio banner")

> The official project can be found in [this repository on
> GitHub](https://github.com/px4/px4-autopilot)

# PX4 Autopilot Septentrio Fork

- [User Documentation](#user-documentation)
    - [Receivers](#receivers)
- [Development Documentation](#development-documentation)

## User Documentation

This is a fork of the PX4 autopilot project. It is used for releases containing Septentrio features
that are not available in official releases yet. No development of features or bugfixes is done in
this repository. Releases can be found under
[releases](https://github.com/septentrio-gnss/Septentrio-PX4-Autopilot/releases). They follow a
standard naming scheme where the first part of the version is the official version, while the second
part shows the specific Septentrio version. For example `v1.14.0-septentrio1` contains Septentrio
fixes on top of the official `v1.14.0` release. Newer versions will have increasing numbers at the
end, like `v1.14.0-septentrio2` or `v1.14.0-septentrio3`. You can download these builds and put them
on your board using QGroundControl, after which you are ready to fly!

To get started with PX4 and a Septentrio receiver, see the [getting started
guide](docs/getting_started.md). For the latest version, [the official user
guide](https://docs.px4.io/main/en/gps_compass/septentrio.html) also contains all the necessary
steps.

**Septentrio only tests specific versions on specific boards. These will be marked as tested. All
the other builds are provided without any testing.**

### Receivers

This is an incomplete list of supported Septentrio receivers for use with autopilots.

* [mosaic-go heading GNSS module evaluation kit](https://web.septentrio.com/l/858493/2022-04-19/xgrp9)
* [mosaic-go GNSS module evaluation kit](https://web.septentrio.com/l/858493/2022-04-19/xgrpd)
* [AsteRx-m3 Pro](https://web.septentrio.com/l/858493/2022-04-19/xgrrz)
* [AsteRx-m3 Pro+](https://web.septentrio.com/l/858493/2022-04-19/xgrs3)

## Development Documentation

Releases follow a standard pattern. A branch is created based on an official release, to which
Septentrio features and bugfixes are added that aren't available in any official release yet.
Releases are then created from those branches. More information can be found in the [release
guidelines](docs/release_guidelines.md).