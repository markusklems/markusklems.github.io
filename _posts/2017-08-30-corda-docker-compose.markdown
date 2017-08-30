---
layout: post
title:  "Corda Setup with Docker Compose"
date:   2017-08-30
categories: corda, docker
---
Recently, I tried out corda, a distributed ledger for financial applications, and have grown to like the system. It is well documented and easy to get started with (if you know kotlin/java). Although it has been criticized for not being a "real" blockchain system, I believe that not everything has to be a blockchain. The greater goal is decentralization which can be realized with different kinds of distributed systems.

It is fairly easy to get started with corda and I was looking into how to build a CorDapp. The suggested approach is in the spirit of test-driven-development to write tests and then do the red-green thing. For incremental development, I am currently looking for a development setup that allows me to have a shorter gap between writing code and seeing changes in the locally running test system. Maybe there is a way to do it but I haven't found it, yet. The tutorials describe how to run a local corda p2p network using a runnodes tool (the code is [here][runnodes], it gets packaged as a runnodes.jar file an can be started with a script).

Eventually, I tried to automate the setup of corda peer-to-peer networks using docker compose ([corda-docker-compose repo][corda-dc-gh]).

The basic setup with 1 controller and 3 nodes works fine.

Then I tried to create an automated setup with the [cordapp-tutorial][cordapp] application. It works, however, only with 1 Controller and 1 Node. If I start an additional node, all nodes start respawning their Java processes. Still trying to figure it out. If you have an idea what I am doing wrong, drop me a line.

[corda-dc-gh]: https://github.com/e-pluribus-unum/corda-docker-compose
[cordapp]: https://github.com/corda/cordapp-tutorial
[runnodes]: https://github.com/corda/corda/blob/master/gradle-plugins/cordformation/src/noderunner/kotlin/net/corda/plugins/NodeRunner.kt