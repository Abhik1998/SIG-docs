# Core components interaction with server and their common end-points
## Overview
  ### Release Signoff Checklist
  The proposal referencing this is given [here](https://github.com/kubernetes/enhancements/blob/master/keps/sig-cluster-lifecycle/wgs/0032-create-a-k8s-io-component-repo.md#history-and-motivation)
  ### Summary
  The aim of this document is to create a new Kubernetes staging repository with minimal dependencies (k8s.io/apimachinery, k8s.io/client-go, and k8s.io/api) and good documentation on how to write a Kubernetes-aware component that follows best practices.
  This document specifically deals with building a package in the new repo that hosts the common code dealing with how the component is doing (e.g. profiling, metrics, current configuration, etc.)
  
  ### Motivation
  The current inconsistency is a headache for many Kubernetes developers, and confusing for end users.Implementation of this will serve it's purpose as mentioned in this [proposal](https://github.com/kubernetes/enhancements/blob/master/keps/sig-cluster-lifecycle/wgs/0032-create-a-k8s-io-component-repo.md#history-and-motivation).
  #### Goals
  - Factor out common HTTPS endpoints describing a component's status.
  - Make the core Kubernetes components utilize these new packages.
  - Have good documentation about how to build a component with a similar look and feel as core Kubernetes components.
  - This repo will host a set of packages needed by the core components in a generic manner, like a **generic toolkit**.
  #### Non-goals
  - Graduate any ComponentConfig API versions (in this proposal).
  - Make this library toolkit a "generic" cloud-native component builder. Such a framework, if ever created, could instead consume these packages.
  - We'll collaborate with higher-level projects like `kubebuilder` and `controller-runtime` though, and let them implement some of the higher-level code out of scope for this repo.
  - Fixing _all the problems_ in the core components, and expanding this beyond what's really necessary.
  - Specifying (in this proposal) _exactly how a Kubernetes component should function_.
