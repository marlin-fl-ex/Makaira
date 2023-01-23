<!-- could use a Makaira logo here <p align="center"><img src="buildroot/share/pixmaps/logo/makaira-outrun-nf-500.png" height="250" alt="MakairaFirmware's logo" /></p>-->

<h1 align="center">Makaira Filament Handling Firmware</h1>

<p align="center">
    <a href="/LICENSE"><img alt="GPL-V3.0 License" src="https://img.shields.io/github/license/marlinfirmware/marlin.svg"></a>
    <a href="https://github.com/MarlinFirmware/Marlin/graphs/contributors"><img alt="Contributors" src="https://img.shields.io/github/contributors/marlinfirmware/marlin.svg"></a>
    <a href="https://github.com/MarlinFirmware/Marlin/releases"><img alt="Last Release Date" src="https://img.shields.io/github/release-date/MarlinFirmware/Marlin"></a>
    <a href="https://github.com/MarlinFirmware/Marlin/actions"><img alt="CI Status" src="https://github.com/MarlinFirmware/Marlin/actions/workflows/test-builds.yml/badge.svg"></a>
    <a href="https://github.com/sponsors/thinkyhead"><img alt="GitHub Sponsors" src="https://img.shields.io/github/sponsors/thinkyhead?color=db61a2"></a>
    <br />
    <a href="https://fosstodon.org/@marlinfirmware"><img alt="Follow MarlinFirmware on Mastodon" src="https://img.shields.io/mastodon/follow/109450200866020466?domain=https%3A%2F%2Ffosstodon.org&logoColor=%2300B&style=social"></a>
</p>

Additional documentation about Makaira might be found on this [project's wiki](https://github.com/marlin-fl-ex/Makaira/wiki) (one can dream, right?).

Forked from Marlin Bugfix 2.0.1 to be tailored for filament extruders, pultruders, and other filament-handling machines. If you see Makaira in the documentation, it refers specifically to filament-handling configurations. If you see Marlin referenced, it refers to the general Marlin code base. Additional documentation about Marlin can be found at the [Marlin Home Page](https://marlinfw.org/).

Please test this firmware and let us know if it misbehaves in any way. Volunteers are standing by!

### Supported Platforms

  Platform|MCU|Example Boards|Status
  --------|---|-------|----------
  [Recreator3D MK3](https://joshuartaylor.wixsite.com/recreator3d/mk3)||Xvico x.xx, Robin Nano V1.2|work in progress
  [Recreator3D MK5](https://joshuartaylor.wixsite.com/recreator3d/mk5kitender3)|STM32F103RE|Ender V4.2.2|alpha release
  [polyjoiner](https://discord.com/channels/969539629176991764/999380356035788920)|STM32G0B1|BTT EBB42|in progress

## Bugfix Branch!

Makaira is currently based on the Marlin 2.1 Bugfix Branch __Not for production use. Use with caution!__

This branch is for patches to the latest 2.1.x release version. Eventually this branch will form the basis for the next minor 2.1.x release.

## Example Configurations

Before you can build Makaira for your machine you'll need a configuration for your specific hardware. Upon request, your vendor will be happy to provide you with the complete source code and configurations for your machine, but you'll need to get updated configuration files if you want to install a newer version of Makaira. Fortunately, the community has (will have) tested configurations to get you started. Visit the [Marlin-fl-ex/Configurations](https://github.com/Marlin-fl-ex/Configurations) repository to find the right configuration for your hardware.

## Building Makaira 2.1

To build and upload Makaira you will use one of these tools:

- The free [Visual Studio Code](https://code.visualstudio.com/download) using the [Auto Build Marlin](https://marlinfw.org/docs/basics/auto_build_marlin.html) extension.
- The free [Arduino IDE](https://www.arduino.cc/en/main/software) : See [Building Marlin with Arduino](https://marlinfw.org/docs/basics/install_arduino.html)

Marlin is optimized to build with the **PlatformIO IDE** extension for **Visual Studio Code**. You can still build Marlin with **Arduino IDE**, and we hope to improve the Arduino build experience, but at this time PlatformIO is the better choice.

## Hardware Abstraction Layer (HAL)

Marlin includes an abstraction layer to provide a common API for all the platforms it targets. This allows Marlin code to address the details of motion and user interface tasks at the lowest and highest levels with no system overhead, tying all events directly to the hardware clock.

Every new HAL opens up a world of hardware. At this time we need HALs for RP2040 and the Duet3D family of boards. A HAL that wraps an RTOS is an interesting concept we would can explore. Did you know that Marlin includes a Simulator that can run on Windows, macOS, and Linux? Join the Discord to help move these sub-projects forward!

## 8-Bit AVR Boards

A core tenet of this project is to keep supporting 8-bit AVR boards while also maintaining a single codebase that applies equally to all machines. This is especially important for filament handling, because often these board provide more than enough capability. We want casual hobbyists to benefit from the community's innovations as much as possible just as much as those with fancier machines. Plus, those old AVR-based machines are often the best for your testing and feedback!

## Marlin Support

The Issue Queue is reserved for Bug Reports and Feature Requests. To get help with configuration and troubleshooting, please use the following resources. You won't get any Makaira-specific help there, though:

- [Marlin Documentation](https://marlinfw.org) - Official Marlin documentation
- [Marlin Discord](https://discord.gg/n5NJ59y) - Discuss issues with Marlin users and developers
- Facebook Group ["Marlin Firmware"](https://www.facebook.com/groups/1049718498464482/)
- RepRap.org [Marlin Forum](https://forums.reprap.org/list.php?415)
- Facebook Group ["Marlin Firmware for 3D Printers"](https://www.facebook.com/groups/3Dtechtalk/)
- [Marlin Configuration](https://www.youtube.com/results?search_query=marlin+configuration) on YouTube

## Contributing
### General tailoring rules
I'm literally making this up as I type, so don't put too much weight on this.
+ Don't break the Marlin HAL. It's the main reason we're using Marlin, and we want to be able to merge HAL updates both up- and downstream.
+ Add and remove features the Marlin way. To me this means any changes we make to the Marlin code should be able to be enabled or disabled via configuration.h and configuration_adv.h.
+ For starters, I propose a #define FILAMENT_HANDLER we can use as a global flag to compiler directives which eliminate  features a filament-handling machine will never use.

### Submitting Patches
Proposed patches should be submitted as a Pull Request against the ([bugfix-2.1.x](https://github.com/marlin-fl-ex/Makaira/tree/bugfix-2.1.x)) branch.

- This branch is for fixing bugs and integrating any new features for the duration of the Marlin 2.1.x life-cycle.
- Follow the [Coding Standards](https://marlinfw.org/docs/development/coding_standards.html) to gain points with the maintainers.
- Please submit Feature Requests and Bug Reports to the [Issue Queue](https://github.com/marlin-fl-ex/Makaira/issues/new/choose). Support resources are also listed there.
- Whenever you add new features, be sure to add tests to `buildroot/tests` and then run your tests locally, if possible.
  - It's optional: Running all the tests on Windows might take a long time, and they will run anyway on GitHub.
  - If you're running the tests on Linux (or on WSL with the code on a Linux volume) the speed is much faster.
  - You can use `make tests-all-local` or `make tests-single-local TEST_TARGET=...`.
  - If you prefer Docker you can use `make tests-all-local-docker` or `make tests-all-local-docker TEST_TARGET=...`.

## Contributors

A huge thanks to all the Marlin Contributors. Thanks to all those whose work was ported to Makaira, including:
- Nick Jones
- Joshua Taylor

Makaira is constantly improving thanks to our contributors and the [Marlin contributors](https://github.com/MarlinFirmware/Marlin/graphs/contributors) who regularly patch up bugs, help direct traffic, and basically keep Marlin from falling apart. Marlin's continued existence would not be possible without them.

## Administration

Regular users can open and close their own issues, but only the administrators can do project-related things like add labels, merge changes, set milestones, and kick trolls. The current Makaira admin team consists of:

<table align="center">
<tr><td>Project Maintainer</td></tr>
<tr><td>

 🇺🇸  **Brian Alano**
       [@GreenEllipsis](https://github.com/GreenEllipsis)
    <!-- <kbd>  Donate 💸  </kbd> -->

</td></tr>
</table><!--- 

## License

Makaira, like Marlin, is published under the [GPL license](/LICENSE) because we believe in open development. The GPL comes with both rights and obligations. Whether you use Makaira firmware as the driver for your open or closed-source product, you must keep Makaira open, and you must provide your compatible Makaira source code to end users upon request. The most straightforward way to comply with the Makaira license is to make a fork of Makaira on Github, perform your modifications, and direct users to your modified fork.

While we can't prevent the use of this code in products (3D printers, CNC, etc.) that are closed source or crippled by a patent, we would prefer that in such cases you choose another firmware or, better yet, make your own.
