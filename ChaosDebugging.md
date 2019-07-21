# Mitchell Kelley and Scott Cranton - Chaos Debugging: Finding and fixing microservice abnormalities

The problem: debugging microservices applications is hard.

A lot of the tooling assumes you're running a monolith

But microservices aren't that (especially if involving multiple teams), so how to get a complete view of the application's state?

"We replaced our monolith with micro services so that eery outage could be more like a murder mystery." -- Honest Status Page


## Squash

Tool that was developed for debugging micro services

Modes:

* Default
    * Deployed to kubernetes, in namespace
    * Adds namespace, connects to existing namespace
    * Squash works with container process to get CRI (pid of process)
* Secure
    * For shared clusters, etc
    * Squash in "operator" mode, watching for a custom resource
    * Debugger launched, connects to container process

Basically, lets you do remote debugging on a remote container

Don't want to set breakpoints in prod tho


## Open Telemetry

They love service meshes

Push things to external proxies

Proxies can handle a lot of the traffic viewing

Ignore requests that are happy path; only want to capture unhappy path requests


## Loop

Capture and dump data based on configuration

Can debug based on context

Docs and Github aren't here yet... something about waiting for TAP/Envoy, "coming soon"

slack.solo.io


## Proactive Debugging

Chaos engineering - put in something harmful so that can be overall healthier

Problems with CE today?
* can be language specific

Service meshes yay.

Can use proxies to simulate application failures

Want things healthy, but not to kill the patient (cascading failures)


## Glueshot

Do Chaos at service mesh level

Runs until stop defined hit

Define error conditions

glooshot.start.io

Also on github


## Best way to start

Getting started w/ service meshes

Build automations against standard interface

servicemeshub.io < site that has overviews of service meshes

