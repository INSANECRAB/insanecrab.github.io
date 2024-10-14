---
title: "Cloud Native: Difference Between Cloud Native and Monolithic Traditional Architecture (modifying)"
categories:
  - cloudnative
tags:
  - cloudnative
  - architecture
  - note
---

What's the key point of both cloud-native and traditional architectures?

* Session status

The difference lies in how to manage session state, such as application and configuration data.
Traditional applications are stateful, meaning that application states are often stored on the compute instance itself. 
To handle this, load balancers typically use a sticky session mechanism to ensure that user requests are routed to the same server. The session variables are retrieved from an external datastore, but the session state itself resides in the instance.

In this method, there's a risk of losing the state, leading to potential inconsistencies. For example, if a specific VM experiences an outage, the load balancer detects this and creates a new session for the user on a different VM. However, the original state, stored on the failed VM, will not be available in the newly created instance.

On the other hand, **Cloud Native Applications** (CNA) are generally stateless. CNAs may process data, but they ensure no data loss experience for users while dynamically managing the number of compute instances. The state in CNAs is stored externally, not inside the VM. 

<mark>The system can dynamically add or remove instances without affecting user experience, as the state is maintained separately in external storage in the CNA.</mark>


In other words traditional architectures typically store session state inside the VM, while only using external storage for lookup purposes, such as user data or session variables. 
In contrast, cloud-native architectures externalize the session state entirely, making it more resilient to VM failures.