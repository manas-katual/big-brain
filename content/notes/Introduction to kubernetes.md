---
title: Introduction to kubernetes
draft: false
tags:
---
Uplink : [[Kubernetes]]

- Kubernetes is an open-source Container management tool which automates container deployment, Container scaling and Load Balancing.
- It schedules, runs and manages isolated containers which are running on virtual/physical/cloud machines.
- All top cloud providers support kubernetes.

## History

- Google developed an internal system called 'borg' (later named as omega) to deploy and manage thousands google applications and services on their Cluster.
- In 2014, google introduced Kubernetes an open source platform written in 'Golang' and later donated by CNF (Cloud native computing foundation).

## Online platform for K8s

- Kubernetes playground
- Play with k8s
- Play with kubernetes classroom

## Cloud based k8s services

- GKE (Google kubernetes service)
- AKS (Azure Kubernetes service )
- Amazon EKS (Elastic kubernetes service)

## Kubernetes installation tool

- Minikube
- Kubeadm

## Problem with scaling up the containers

- Containers cannot communicate with each other
- Autoscaling and Load Balancing was not possible
- Containers had to be managed carefully

## Features of kubernetes

- Orchestration ( clustering of any number of containers running on different networks )
- Autoscaling
- Auto-Healing
- Load Balancing
- Platform independent ( Cloud/Virtual/Physical )
- Fault Tolerance ( Node/POD failure )
- Rollback ( going back to previous version )
- Health monitoring of containers 
- Batch execution ( Onetime, sequential, parallel )

## Difference between Kubernetes and docker swarm


| Features                               | Kubernetes                                                                   | Docker Swarm                                                          |
| -------------------------------------- | ---------------------------------------------------------------------------- | --------------------------------------------------------------------- |
| Installation and Cluster configuration | Complicated and time consuming                                               | Fast and easy                                                         |
| Support                                | K8s can almost work with all container types like Rocket, Docker, Containerd | works with docker only                                                |
| GUI                                    | GUI Available                                                                | GUI not Available                                                     |
| Data volumes                           | Only shared with containers in same POD                                      | Can be shared with any other container                                |
| Updates & Rollbacks                    | Process scheduling to maintain services while updating                       | Progressive updates & service health monitoring throughout the update |
| Autoscaling                            | support vertical and horizontal autoscaling                                  | Not support Autoscaling                                               |
| Logging and monitoring                 | Inbuilt tool present for monitoring                                          | used 3rd party tools like splunk                                      |
