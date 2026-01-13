# Project homelab

This repository documents the design and implementation of my personal homelab. It is maintained as living documentation with a focus on reprodicibility, learning and skill development.

## Purpose

The homelab is used to explore infrastructure concepts, networking and operational practices.

## Goals

- Build and operate a maintainable homelab using production based practises
- Document decisions, dependencies and summaries of installation and configuration, not just installation steps
- Enable rebuilds from documentation fully or partially
- Develop skills in networking, virtualization, service operations and documentation 

## Scope

The environment is build on single Proxmox host running multiple services primarily as LXC containers. Services are designed to be independently rebuildable and documented with dependency and configuration boundaries.

Architectural decision records are recorded to preserve context of architectural choices.

## Architecture summarie

- Hypervisor: Proxmox VE
- Workloads: LXC containers
- Networking: Static addressing for core devices and services
- Core services: DNS (Pi-hole), reverse proxy (NPM), VPN (WireGuard)

## Repository structure

TBD