# Containerisation

## What is Docker?

Docker ensures that applications run in the same environment across different machines by packaging the application together with its dependencies, runtime libraries, and configuration.

Docker does not include the operating system kernel. Containers share the host OS kernel.

---

## Containerisation Concept

Containerisation allows applications to run in isolated environments called containers.

Common tools in the container ecosystem:
- Docker: building and running containers
- Kubernetes: container orchestration and management

---

## Why Docker Exists: Virtual Machines vs Containers

### Virtual Machines (VMs)

Virtual machines run applications by virtualizing hardware.

Characteristics:
- Each VM contains a full operating system
- Strong isolation
- High resource consumption
- Slow startup time
- Inefficient use of system resources

VMs are suitable when strong isolation is required, but they are expensive in terms of CPU and memory.

---

### Containers

Containers virtualize the operating system instead of hardware.

Characteristics:
- Containers do not include a full OS
- Containers share the host OS kernel
- Fast startup
- Low memory usage
- High deployment efficiency

Containers are lightweight compared to virtual machines and are ideal for modern application deployment.

---

## Dockerfile vs YAML Configuration

Dockerfile:
- Describes how to build a Docker image
- Defines base image, dependencies, and runtime instructions

YAML configuration files:
- Used by Docker Compose or Kubernetes
- Define how containers are deployed, connected, and managed

---

## Linux and Docker

Docker relies on Linux kernel features such as:
- Namespaces for process isolation
- cgroups for resource management
- Union filesystems for layered images

Because of this:
- Docker runs natively on Linux
- Docker on macOS and Windows runs inside a lightweight Linux virtual machine

---

## Application Deployment with Docker

A Docker image contains:
- Application code
- Runtime dependencies
- System libraries
- Configuration

A container is a running instance of a Docker image. Multiple containers can be created from the same image.

Each container runs in isolation and communicates with other containers through defined network interfaces.

---

## Comparison Summary

| Feature | Virtual Machine | Container |
|-------|----------------|-----------|
| Operating system | Full OS per VM | Shared host kernel |
| Startup time | Slow | Fast |
| Resource usage | High | Low |
| Isolation level | Strong | Process-level |
| Portability | Medium | High |

---

## Key Takeaway

Docker solves the problem of inconsistent application behavior across environments by standardizing the runtime environment using lightweight containers.