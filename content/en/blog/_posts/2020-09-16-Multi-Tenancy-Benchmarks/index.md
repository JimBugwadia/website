---
layout: blog
title: "Multi-Tenancy Benchmarks"
date: 2020-09-16
slug: multi-tenancy-benchmarks
---

**Authors**: Anuj Sharma (...), Divya Rani (...), Jim Bugwadia (Nirmata)

Kuberetes was designed to manage workloads across pools of infrastructure and hence decouple applications lifecycles from infrastructure. However, configuration complexity often gets in the way of sharing clusters across teams and applications leading to cluster sprawl and wasted resources.

The [Kubernetes Multi-Tenancy Working Group](https://github.com/kubernetes-sigs/multi-tenancy) is chartered with exploring and defining multi-tenancy models for Kubernetes. Within this group, the [Multi-Tenancy Benchmarks (MTB)](https://github.com/kubernetes-sigs/multi-tenancy/tree/master/benchmarks) initiative is working on guidelines for securely sharing clusters within an enterprise and providing tools to measure conformance.

In this post, we will introduce a Multi-Tenancy Benchmarks, along with a validation tool that automates behavioral and configuration checks on a namespace and reports complaince to multi-tenancy guidelines.

## Multi-Tenancy Benchmarks

The Multi-Tenancy Benchmarks define three profile levels and seven categories for tests.

### Multi-Tenancy Profile Levels

Profile Levels define varying grades of multi-tenancy.  Level 1 and 2 provide (soft) multi-tenancy suitable for teams within an enterprise, while Level 3 is targeted for (hard-er) multi-tenancy with complete isolation required by service providers.

* **Profile Level 1**: namespace based isolation and segmentation with pod security
* **Profile Level 2**: meets Level 1 and also allows self-service operations across multiple namespaces
* **Profile Level 3**: meets Level 2 and also allows full isolation across tenants

The current focus is on Profile Level 1 and 2. 

### Multi-Tenancy Categories

Categories define the various areas of multi-tenancy concerns:

* **Control Plane Isolation**: runtime isolation and protection of cluster resources from tenants. 
* **Tenant Isolation**: isolation across tenants.
* **Network Isolation**: network security to provide isolation across tenant namespaces for ingress and egress traffic.
* **Host Isolation**: container hosts are protected from tenant workloads.
**Data Isolation (DI)**: tenant data, including volumes and secrets, cannot be accessed by other tenants.
**Fairness**: fair usage of shared resources.
**Self-Service Operations**:  allowance for tenants to manage their own resources.

### Multi-Tenancy Tests

There are currently 17 PL1 tests and 3 PL2 tests defined:

#### Profile Level 1 Tests

* Block access to cluster resources
* Block Multitenant Resources
* Block add capabilities
* Require run as non-root user
* Require image pull always
* Require PVC reclaim policy delete
* Require CAP_DROP_ALL
* Block privileged containers
* Block privilege escalation
* Configure namespace resource quotas
* Configure namespace object limits
* Block use of host path volumes
* Block use of NodePort services
* Block use of host networking and ports
* Block use of host PID
* Block use of host IPC
* Block modification of resource quotas

#### Profile Level 2 Tests

* Create Role Bindings
* Create Network Policies
* Create Namespaces


## Validating Multi-Tenancy

The `kubectl-mtb` tool is designed to automate running Multi-Tenancy Benchmarks checks and reporting results. It is designed to be easy to use as a command line tool or as a CronJob. 





## Future Work


---

_[Anuj Sharma](...) ..._

_[Divya Rani](...) ..._

_[Jim Bugwadia](https://twitter.com/JimBugwadia) is a founder at Nirmata, and a contributor to the Kubernetes multi-tenancy and policy working groups._