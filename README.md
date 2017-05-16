# Go Wrapper for ZFS #

Simple wrappers for ZFS command line tools.

[![GoDoc](https://godoc.org/github.com/tomi-engel/go-zfs?status.svg)](https://godoc.org/github.com/tomi-engel/go-zfs)

## Fork Introduction

This is a fork of the original [go-zfs project](https://github.com/mistifyio/go-zfs) in order to get our [zfs_exporter](https://github.com/tomi-engel/zfs_exporter) project up and running.

Consider this as an __evil hack__.

> Please use the original [go-zfs project](https://github.com/mistifyio/go-zfs) … not this code!


The rest of this README is mainly taken straight from the `go-zfs` project:

## Requirements ##

You need a working ZFS setup.  To use on Ubuntu 14.04, setup ZFS:

    sudo apt-get install python-software-properties
    sudo apt-add-repository ppa:zfs-native/stable
    sudo apt-get update
    sudo apt-get install ubuntu-zfs libzfs-dev

Developed using Go 1.8.1

Generally you need root privileges to use anything zfs related.

## Status ##

This has been only been tested on Ubuntu 14.04 and older SmartOS releases.

In the future, we hope to work directly with libzfs.

# Hacking #

The tests have decent examples for most functions.

```go
//assuming a zpool named test
//error handling ommitted


f, err := zfs.CreateFilesystem("test/snapshot-test", nil)
ok(t, err)

s, err := f.Snapshot("test", nil)
ok(t, err)

// snapshot is named "test/snapshot-test@test"

c, err := s.Clone("test/clone-test", nil)

err := c.Destroy()
err := s.Destroy()
err := f.Destroy()

```

# Contributing #

See the [contributing guidelines](./CONTRIBUTING.md)

