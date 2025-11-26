+++
date = '2025-05-04T09:22:06+08:00'
draft = true
title = 'Container Orchestration'
+++

# Basics

## Why

## How

## What

## When

## Who

### Docker Compose vs Kubernetes

## Terminology

- Cluster
  Entire Kubernetes system (i.e. nodes, pods, services, Kubernetes processes)
- Node
  Single physical/virtual machine that runs containers
- Pod
  Smallest deployable unit in Kubernetes (usually, 1 container)

```
Cluster
├── Node 1
│   ├── Pod A
│   ├── Pod B
│   └── Pod C
├── Node 2
│   ├── Pod D
│   └── Pod E
└── Node 3
    ├── Pod F
    ├── Pod G
    └── Pod H
```

# Bare Bones Setup

## Minikube + Docker

Minikube is a lightweight Kubernetes ...
Docker automates away the need to create boilerplate code by pulling images.

### What is needed

- Manifest
  The YAML file needed for Kubernetes

# Under the hood of Kubernetes

## Visual Representation

```
Kubernetes System
├── Control Plane
│   ├── API Server
│   ├── etcd
│   ├── Scheduler
│   └── Controller Manager
│
├── Worker Nodes
│   ├── kubelet
│   ├── kube-proxy
│   └── Container Runtime
│
├── Workloads
│   ├── Pods
│   ├── Deployments
│   └── Services
│
└── Networking & Storage
    ├── Services
    ├── Ingress
    └── Persistent Volumes
```

## What happens when Kubernetes

1. API Server receives YAML (when we run `kubectl apply -f file-name.yaml`)
2. etcd stores the desired state
3. Scheduler picks nodes for pods
4. kubelet pulls images & starts containers
5. kube-proxy sets up network rules
6. Controller ensures replicas stay running
7. Service creates load balancing rules
