## ClinGen Single Sign-on Platform

Status: Proposed

### Context

We would like to implement a single sign-on platform for software products in the ClinGen ecosystem to address the following concerns:

* Users are frustrated by having to maintain multiple accounts and passwords to log into different applications within ClinGen.
* The lack of a consistent user identity makes it more challenging to design applications that interoperate across the ClinGen ecosystem.

https://docs.google.com/presentation/d/18TmPzghhE1OzoxG1CwviUOyu8LXFeGYt/edit?slide=id.g2cbf06db267_0_91#slide=id.g2cbf06db267_0_91

https://broadinstitute.atlassian.net/browse/CGSP-725?atlOrigin=eyJpIjoiNTFlOWZmODNlOWIwNGZlMDkwMmY0ZWQ1ZTlmZGQxOTgiLCJwIjoiaiJ9

### Decision

### Alternatives

#### Separate Platforms, User IDs shared via Data Exchange

Each group maintains its own authentication platform. When new users are created, IDs are broadcast over the Data Exchange so that other platforms can pick up other user IDs in ClinGen. When user IDs are shared this way, systems should include all known IDs for the given user in other systems, so that it is possible to link users identities across platforms.

##### Pros

* Agreeing on a single platform that meets the needs of every group is difficult.
* Adopting a single solution limits the design choices of other groups in the future.

##### Cons

* Requires complex integration to achieve interoperability
* Email/Password based auth still unique per-application
* Merging duplicate users likely to be difficult and inconsistent
* Can't share authentication tokens across applications

#### Firebase Auth

Each group has an application within a single Firebase account. Firebase User IDs become the common identifier for users of ClinGen systems.

##### Pros

* Well established platform from major cloud vendor
* Multple teams have some experience successfully integrating auth
* Pricing is reasonable for our use case
* Should be able to share authentication tokens across applications
* Good security track record

##### Cons

* Developer experience is sub-optimal
* Authorization external to platform

#### WorkOS

Each group has an application within a single WorkOS account. WorkOS User IDs become the common identifer for users of ClinGen systems.

##### Pros

* Authorization included as part of the platform
* Stanford team reports initial good developer experience
* Has enhanced B2B integrations with MCP auth

##### Cons

* No other teams have tested this yet
* Product of small startup
* Unknown security history
* Target market (SaaS companies targeting enterprise customers) doesn't exactly fit ClinGen's needs.

#### Amazon Cognito

Leverage existing authentication platform at Stanford supporting GCI/VCI. Add social login (Google/Microsoft) ; Amazon IDs become common user IDs across ClinGen applications.

##### Pros

* Well established platform from major cloud vendor
* Currently integrated in GCI/VCI
* Should be able to share authentication tokens across applications
* Good security track record

##### Cons

* Stanford wants to migrate from this (please let us know your reasons)

#### Do nothing

The cost of attempting a single sign-on may be too high to justify the benefit. Achieving buy-in to any one of these solutions may not be feasible.

### Consequences

The choice of implementation is a far-reaching decision that will impact most software systems in ClinGen and impose significant design constraints. Once we have committed to a platform it will be difficult, though not impossible, to coordinate a change to a different system should the need arise. This is an architectural decision that requires careful consideration and agreement between interested groups.
