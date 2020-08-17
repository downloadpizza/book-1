---
layout: content
title: Nu Installieren
prev: Table of Contents
next: Introduction
link_prev: /de/inhaltstabelle.html
link_next: /de/einleitung.html
---

<-- TODO: WIP --!>

Der derzeit einfachste Weg Nu zum laufen zu bringen, ist es, es durch [crates.io](https://crates.io) zu installieren, vorkompilierte binaries von der [release Seite](https://github.com/nushell/nushell/releases) herunterzuladen, oder einen vorgebauten Docker container zu verwenden.

## Vorkompilierte binaries

Du kannst fertig kompilierte Nu binaries von der [release Seite](https://github.com/nushell/nushell/releases) herunterladen. Alternativ kannst du unter MacOS auch [Homebrew](https://brew.sh/) verwenden in dem du `brew install nushell` ausführst.

### Windows

**Wichtig:** Nu funktioniert derzeit nur in Windows 10 und hat keinen Support für Windows 7/8.1.

Lade die neuste `.zip`-Datei von der [release Seite](https://github.com/nushell/nushell/releases) und extrahiere sie zum Beispiel nach:

{% include installation/windows_example_extraction_location.md %}

Füge nun den Order in dem sich `nu` befindet der `PATH` Umgebungsvariable hinzu. Danach solltest du den `nu` Befehl verwenden können um Nu zu starten:

{% include installation/windows_run_nu.md %}

Wenn du das neue [Windows Terminal](https://github.com/microsoft/terminal) verwendest kannst du `nu` hinzufügen indem du:

{% include installation/windows_terminal_default_shell.md %}

in die `"profiles"` liste in der Windows Terminal Config JSON Datei anfügst. Weiters kannst du das `"defaultProfile"` ändern mit:

{% include installation/windows_change_default_profile.md %}

Jetzt sollte `nu` standardmäßig starten wenn du Windows Terminal ausführst.

## Vorgebaute Docker container

Wenn du einen fertigen Docker container haben willst, kannst du auf Quay.io mit dem tag [nushell organization](https://quay.io/organization/nushell) nach fertigen Containern suchen.
Einen container aufzusetzen sollte circa so aussehen:

{% include installation/pull_prebuilt_container.md %}

"nu-base" und "nu" haben eine `nu` binary, aber "nu-base" beinhaltet auch den Quellcode im Pfad `/code`.

Du kannst den container auch lokal kompilieren mit den zur Verfügung gestellten [dockerfiles](https://github.com/nushell/nushell/tree/master/docker):
Um das base image zu bauen:

{% include installation/build_containers_locally_base_image.md %}

Und um den kleinen container (mit mehrstufiger Kompilation) zu bauen:

{% include installation/build_containers_locally_multistage_build.md %}

In beiden Fällen kannst du den Container ausführen mit:

{% include installation/run_containers_built_locally.md %}

Der zweite container "nu" ist etwas kleiner, falls Größe wichtig ist.

## Vorbereiten

Before we can install Nu, we need to make sure our system has the necessary requirements. Currently, this means making sure we have both the Rust toolchain and local dependencies installed.

### Installing a compiler suite

For Rust to work properly, you'll need to have a compatible compiler suite installed on your system. These are the recommended compiler suites:

* Linux: GCC or Clang
* macOS: Clang (install Xcode)
* Windows: [Visual Studio Community Edition](https://visualstudio.microsoft.com/vs/community/)

For Linux and macOS, once you have installed the compiler, you are ready to install Rust via `rustup` (see below).

For Windows, when you install Visual Studio Community Edition, make sure to install the "C++ build tools" as what we need is `link.exe` which is provided as part of that optional install.  With that, we're ready to move to the next step.

### Installing Rust

If we don't already have Rust on our system, the best way to install it via [rustup](https://rustup.rs/). Rustup is a way of managing Rust installations, including managing using different Rust versions. 

Nu currently requires the **latest stable (1.43 or later)** version of Rust. The best way to let `rustup` find the correct version for you. When you first open `rustup` it will ask what version of Rust you wish to install:

{% include installation/rustup_choose_rust_version.md %}

Once we are ready, we press 1 and then enter.

If you'd rather not install Rust via `rustup`, you can also install it via other methods (e.g. from a package in a Linux distro). Just be sure to install a version of Rust that is 1.39 or later.

## Dependencies

### Debian/Ubuntu

You will need to install the "pkg-config" and "libssl-dev" package:

{% include installation/install_pkg_config_libssl_dev.md %}

Linux users who wish to use the `rawkey` or `clipboard` optional features will need to install the "libx11-dev" and "libxcb-composite0-dev" packages:

{% include installation/use_rawkey_and_clipboard.md %}

### RHEL

You'll need to install "libxcb", "libssl-dev", and "lib11-dev".

### macOS

Using [Homebrew](https://brew.sh/), you will need to install the "openssl" and "cmake" using: 

{% include installation/macos_deps.md %}

## Installing from [crates.io](https://crates.io)

Once we have the dependencies Nu needs, we can install it using the `cargo` command that comes with the Rust compiler.

{% include installation/cargo_install_nu.md %}

That's it!  The cargo tool will do the work of downloading Nu and its source dependencies, building it, and installing it into the cargo bin path so that we can run it.

If you want to install with more features, you can use:

{% include installation/cargo_install_nu_more_features.md %}

For all the available features, the easiest way is to check out Nu and build it yourself using the same Rust tools:

{% include installation/build_nu_yourself.md %}

For this to work, make sure you have all the dependencies (shown above) on your system.

Once installed, we can run Nu using the `nu` command:

{% include installation/crates_run_nu.md %}

## Building from source

We can also build our own Nu from source directly from github. This gives us immediate access to the latest Nu features and bug fixes.

{% include installation/git_clone_nu.md %}

Git will clone the main nushell repo for us. From there, we can build and run Nu if we are using `rustup` with:

{% include installation/build_nu_from_source.md %}

You can also build and run Nu in release mode:

{% include installation/build_nu_from_source_release.md %}

People familiar with Rust may wonder why we do both a "build" and a "run" step if "run" does a build by default. This is to get around a shortcoming of the new `default-run` option in Cargo, and ensure that all plugins are built, though this may not be required in the future.

## Setting as your login shell

**!!! Nu is still in development, and may not be stable for everyday use. !!!**

To set the login shell you can use the [`chsh`](https://linux.die.net/man/1/chsh) command.
Some Linux distributions have a list of valid shells located in `/etc/shells` and will disallow changing the shell until Nu is in the whitelist. You may see an error similar to the one below if you haven't updated the `shells` file:

{% include installation/chsh_invalid_shell_error.md %}

You can add Nu to the list of allowed shells by appending your Nu binary to the `shells` file.
The path to add can be found with the command `which nu`, usually it is `$HOME/.cargo/bin/nu`.
