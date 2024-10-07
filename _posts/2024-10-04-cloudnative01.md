---
title: "Cloud Native : difference between cloud native and monolithic traditional architecture (modifying)"
categories:
  - cloudnative
tags:
  - cloudnative
  - architecture
  - note
---

What's the key point of both cloud native and traditional architecture?

* session status

The difference is how to deal with the session status, such as application and setting data.
The traditional application has state.
Most commonly the application state is stored in the compute instance.
So the load balancer has used sticky session to route customer request to the same server.
The load balancer could forward traffic of specific user to the same instance by using sticky session and the user information,
could be searched as session variable in the external datastore.

In this method there's a possibility to miss the state so incorrect status can happen.