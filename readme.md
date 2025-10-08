## Content

this repo contains infrastructure resources and team definitions for experimental systems

all backstage entities will be in namespace `experiments`, for all references use full qualified name <kind>:<namespace>/<name>
all entities have appropriate team ownership based on responsibility area

## Resources

### Infrastructure Resources

* **Kind: Resource, type: k8s-cluster**
  * k8s-cluster-production - Production Kubernetes cluster
  * k8s-cluster-staging - Staging Kubernetes cluster  
  * k8s-cluster-development - Development Kubernetes cluster
  * owner: group:experiments/team-infrastructure

* **Kind: Resource, type: virtual-machine-windows** 
  * dev1vmgcighl01 - MSSQL database VM for development
  * prod1vmgcighl01 - MSSQL database VM for production
  * stg1vmgcighl01 - MSSQL database VM for staging
  * owner: group:experiments/team-infrastructure

* **Kind: Resource, type: mssql-database-server**
  * purple-mssql-database-server - MSSQL server instance (spans multiple VMs)
  * owner: group:experiments/team-database
  * dependsOn:
    * resource:experiments/dev1vmgcighl01
    * resource:experiments/prod1vmgcighl01  
    * resource:experiments/stg1vmgcighl01

## Groups

* **Kind: Group, type: experimental-team**
  * team-database - Database administration team
  * team-infrastructure - Infrastructure and platform team
  * team-platform - Platform engineering team
  * team-alpha - Development team Alpha
  * team-bravo - Development team Bravo

## Structure

```
experimental_bordel/
├── catalog-info.yaml (Location entities with wildcard references)
├── resources/
│   ├── databases.yaml (Database servers)
│   ├── virtual-machines.yaml (VM resources) 
│   └── k8s-clusters.yaml (Kubernetes clusters)
└── groups/
    └── teams.yaml (All team groups)
```

## Purpose

This repository serves as the foundation infrastructure catalog for the experimental systems, providing:
- Kubernetes clusters for different environments
- Database infrastructure (VMs and server instances)
- Team definitions and organizational structure
- Resource dependencies and ownership mapping
