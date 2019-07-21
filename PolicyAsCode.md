# Torin Sandall - Styra - Policy As Code

github.com/open-policy-agen/opa

github.com/tsandall/oscon-2019

openpolicyagent.org

When things don't work, developers need to access system to check

Need to have checks so that Alice can't take down a service or access Bob's PII

So... AuthZ on all the things

But, how do you enforce policy changes?  Roll-out the changes?  Test policies?  And if you have 100+ services in various languages?

OPA: Unified Policy Enforcement Across the Stack

Need to make policies written and understood by human and machine

Domain agnostic

OPA: General-purpose policy engine

Decouple policy decision making from enforcement

Ex:

    default allow = false
    allow = true { input.method = "GET"; input.path = ["salary", id]; input.user = id }
    allow with input as {"method": "GET", "path": [ "salary", "bob"], "user": "bob"} // true
    allow with input as {"method": "GET", "path": [ "salary", "alice"], "user": "bob"} // false

Can embed opa as a library in application, or run as daemon and query over HTTP

"Host local cache for policy decisions" < so recommended to run as close to application as possible

    curl localhost:8181/v1/data/repl/allow?pretty -d @allowed.json      // true
    curl localhost:8181/v1/data/repl/allow?pretty -d @disallowed.json   // false

play.openpolicyagent.org

Web IDE for writing and evaluating policies

Basically, it seems to work best for validating your config based on OPA code/policies... I guess?  And "hey should this user be able to access this thing" via api calls.  And being able to unit test policies.

Apparently CapitalOne uses this tool w/ Kubernetes