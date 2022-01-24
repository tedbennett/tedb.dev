---
title: "Transmission"
date: 2022-01-24T09:04:06Z
description: "Remote controller for Transmission CLI"
icon: "fas fa-file-download"
github: "https://github.com/tedbennett/transmission-controller"
largeImages:
  - "https://tedb-dev.s3.eu-west-2.amazonaws.com/transmission/transmission-1.png"
techStack:
  - "Rust"
  - "React"
  - "Rocket"
  - "Transmission CLI"
---

WebUI client for Transmission CLI that can control a remote instance of the Transmission BitTorrent client. It can also (rudimentally) check the connection to a VPN (if at a static IP).

The frontend is very basic and was written with React using Bootstrap CSS, and the backend was written in Rust using the Rocket web framework. I'm learning how to use Rust at the moment and am loving it - I see a lot of nice similarities with Swift as well as some nice differences and a lot more platforms to target.

I'm planning to expand this to neatly Dockerise it so that it can be more easily set up.
