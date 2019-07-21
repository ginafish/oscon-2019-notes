# Alex Borysov, Mykyta Protsenko - Netflix - Break me if you can: practical guide to building fault-tolerant systems

What is fault-tolerance?

Fault != error != failure

Lots of layers to components

Fault: incorrect internal state

Error: visibly incorrect behavior (still works by and large)

Failure: main functionality is broken
; blackout

So, fault tolerance means working even with _faults_

Titanic:
* Fault: hitting iceberg
* Error: Water in the hull
* Failure: Sinking

Miracle on the hudson
* Fault: hitting geese
* Error: Engine shut down
* Failure: None!

Errors will still happen in fault tolerance systems, but should not have failure


# Dodging geese
GRPC API gateway -> Geese service
                -> Clouds service
                -> Leaderboard service

GRPC recommended

Geese and clouds are fixtures

Async is good

Latencies add up - can we predict them?
* Hence, we should use timeouts - adds predictable latencies

REST - should always be nonblocking

Demo - geese and clouds were missing, leaderboard blinking


# Observability
Monitor: QPS, latency, errors

OpenCensus - metric reporter from Google, OSS, can export

Don't overdo it on metrics

But, metrics aren't enough!

Distributed tracing adds additional insight

OpenTelemetry - available tool for distributed tracing


# Partial Degradation

Clouds are slow, geese are fast, need to fix

Shouldn't fail if one small piece fails!

So, let's retry?

Retries are good for intermittent failures, good for users

Cloud calls don't prevent geese from arriving

Why retry leaderboard and not cloud?  Clouds are so slow that if we keep retrying, it will make it even worse.  Ex: retry on network faults, but not failures.  Avoid retry storms!

Exponential Backoffs - sometimes, services need time and patience to fix

Fallbacks

Circuit breaker - things dying, have backup

On Error:
* retry
* fallback
* fail fast

Retry is a product decision - only important things

Don't want to retry slow calls

Tail tolerance - request that is 200ms, after 100ms of no response, do a second request, and then take the fastest of the two

"Request hedging" - 99%ile latency + 100 requests -> 1% failure w/ tail tolerance


# Error Handling

Don't process failed calls

Be mindful of deadlines
* Client makes a req w/ 200ms timeout, api gateway takes 120ms, destination takes 90ms, api gateway keeps trying even after client has given up

Solution: deadline propagation

API gateway should be mindful of client's deadline.  It won't keep trying to hit destination after the time it knows the client will be waiting for

Predictable throughput? Are we exceeding limits?

Concurrency Limits - Netflix's library for limiting throughputs
* Can partition limits so that premium geese given more throughput

oscon.breakit.xyz


# Monitoring

Ex: If no updates to leaderboard, we know that means something broken

But... with all this, we might not necessarily know that the application is usable

Prober
* Checks availability
* Latency
* Response verification
cloudprober.org

Blackbox, check application works from consumer's point of view

Should also check vs baseline (what if there are too many geese?!)

If have a bad release, should have easy rollbacks

Technical solutions not enough.  Communicate with your team!

Should be easy to communicate whatever you notice.  Establish roles and communication channels ahead of time.  How to bring people in, how to escalate, who's on the hook and when.

Don't be afraid to overcommunicate!

Postmortems
* Should be blameless, constructive
* Focus on what to do to avoid repeating
* Can make it a social postmortem

Structure of a postmortem:
* Timeline
* Causes
* Remedies

Automatic rollbacks based on metrics/monitoring

Learn from failures
Blameless postmortem
Alert playbooks
Build knowledgebase
Share it!

