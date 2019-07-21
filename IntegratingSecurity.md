# Lucas Charles - GitLab - Integrating Security Into Modern Software Development: A Workflow Study

@theoretick
Consultant for testability and CD

## The problem (why this is hard)
Building securely is hard.  Constantly have to update while getting into Agile/iteration/etc process changes
Security process integration ->> cheaper
"Shift Left" security and scalability
Applications are prime targets
Code changes are happening faster (thanks agile)
App Sec tools are expensive and require much integration - but we need to start doing it

Iterative development does not work with "test everything" flows
    Have to plug in a build system
    Vulnerabilities are not static, so one on line 12 will not be on line 12 tomorrow
    Thus, need to integrate with code review process
Security and dev teams still do not communicate
    Need to shift where and who on security scans
    Roles need to be more complimentary - enable devs to participate in security process
Complex tooling :(
    Users have to develop workflows, edges
    Tools usually only do one thing and one thing well
Teams need to collaborate without seperate mental work spaces


## Methods
SAST lite in IDE
    like "don't use this hash algorithm, bits aren't as random, use another"
Static Analysis
Software Composition Analysis
    secure libraries? etc
Dynamic Analysis
    full running application being scanned
Manual Penetration Test


## Process
Traditional Process (siloed):
Dev -> repo -> feature branch ci -> master branch ci -> CD -> Test environment -> DAST/IAST report -> security team -> dismiss or create issue (ignore false positives on vulnerabilities) -> ticket to devs
Pointing fingers, recurring behavior, affects what features go out, intensive (have to go through a couple of cycles), and requires heavy context switching for both teams
But... when is a code vulnerability a vulnerability? As soon as it gets pushed to master!
Enhancing IT security more of a priority than DevOps, but 46% have only a partially developed DevOps strategy

Security should be empowreing, not blocking
Address vulnerabilities during software development, not post-deploy
Pro-Active security culture - target
Vulns reported directly to accountable devs
Minimal context switching

Tools
Need to avoid warning fatigue
Run scans before merge - they belong in the test stage next to unit tests

Updated Process:
dev -> repo -> feature -> review app -> security testing in pipeline report -> dev
                        -> merge to master -> CD -> deploy -> security dashboard -> security team -> create or dismiss issue
Security tests at feature and master branch CI steps

Advantage:
    Contextual - devs immediately address what currently working on, not what was working a while ago
    Integrated & congruent w/ DevOps tools and processes
    Better use of security team's time

"Your most important security product won't be a security product" - VMWare CISO


## What next?
Security approvals in merge requests
Show on dashboard when security tests are not ran
Forbit push to remote if commit contains secrets

bit.ly/osconsecworkflow
bit.ly/osconsecworkflowwhitepaper