# The Practical 3-Month DevOps Engineer Roadmap
### From Zero to Job-Ready-ish: Build → Automate → Deploy → Monitor → Troubleshoot → Secure → Document

**Time budget:** ~20–22 hrs/week (3 hrs weekdays, 4 hrs weekends)
**Format:** Concepts, structure, exercises, and checklists only — **no code is provided**. You write every line yourself.

---

## TABLE OF CONTENTS

1. Career Target
2. Prerequisites
3. DevOps Skill Tree
4. 12-Week Roadmap
5. Daily Schedule System
6. Month 1 — Foundations (Linux, Networking, Git, Bash, Docker)
7. Month 2 — Automation & Cloud (CI/CD, AWS, Terraform)
8. Month 3 — Production Skills (Kubernetes, Monitoring, Security)
9. AI for DevOps
10. Four Portfolio Projects
11. Troubleshooting Training (30 Scenarios)
12. Interview Question Bank
13. Full Mock Interview Simulation
14. Job Application Strategy
15. Resume Strategy
16. GitHub Portfolio Strategy
17. Learning Tracker (12-Week Checklist)
18. Learning Resources
19. Certifications
20. What NOT to Learn Yet
21. Months 4–12 Roadmap
22. Final Job-Readiness Exam & Skill Matrix
23. Realistic Expectations

---

## 1. CAREER TARGET

### Roles to target after this roadmap

| Job Title | What the role does | Key skills | Beginner difficulty | Weeks that prepare you | Primary/Secondary |
|---|---|---|---|---|---|
| DevOps Engineer Trainee | Supports pipelines, basic infra tasks, learns on the job | Linux, Git, Docker, basic CI/CD | Easy–Medium | 1–8 | **Primary** |
| Junior DevOps Engineer | Builds/maintains CI/CD, small infra changes | Docker, CI/CD, basic AWS, Terraform basics | Medium | 1–10 | **Primary** |
| Cloud/DevOps Engineer (junior) | Mix of cloud infra + deployment work | AWS core services, Terraform, CI/CD | Medium | 5–10 | **Primary** |
| Cloud Support Engineer | Diagnoses cloud issues, tickets, some automation | AWS fundamentals, networking, Linux | Easy–Medium | 1–7 | **Primary** |
| Junior Cloud Engineer | Provisions and maintains cloud resources | AWS, IaC basics, networking | Medium | 5–9 | **Primary** |
| Build & Release Engineer | Owns build pipelines, artifact/versioning | CI/CD, Git, scripting | Medium | 4–6 | Secondary |
| Junior Infrastructure Engineer | Manages servers, networking, some IaC | Linux, networking, Terraform | Medium | 1–9 | Secondary |
| Junior SRE | Reliability, monitoring, incident response | Monitoring, Kubernetes basics, Linux | Medium–Hard | 9–12 | Secondary |
| Platform Engineer Trainee | Builds internal tooling/platforms | Kubernetes, IaC, CI/CD | Hard for fresher | 9–12 | Secondary |
| DevSecOps Trainee | Security-focused pipeline/infra work | Security basics, CI/CD, IAM | Medium–Hard | 9–12 | Secondary |

### Learning vs. interview-ready vs. job-ready vs. professional experience

These are **four different things** — don't conflate them:

- **Learning the skills** — you understand concepts and can follow along with labs. This is where most of this roadmap gets you by week 8–9.
- **Interview-ready** — you can explain concepts clearly, answer "what would you do if…" questions, and defend your own projects under pressure. This requires deliberate practice (Part 12–13), not just knowledge.
- **Job-ready** — you can be dropped into an unfamiliar but reasonably documented environment and be productive within weeks, handling ambiguity and unfamiliar tools. Junior job-ready is achievable with strong projects + fundamentals; it is not the same as senior job-ready.
- **Professional experience** — real production systems, real incidents, real teammates, real business constraints, real consequences for mistakes. **No roadmap or self-study substitutes for this.** Your first job is where this actually starts.

**Honest note:** 3 months of disciplined study can realistically get you to "interview-ready for trainee/junior roles with solid projects." It does **not** guarantee a job — hiring also depends on market conditions, competition, location, and how you present yourself. Treat month 4 onward as continued sharpening while you apply.

---

## 2. PREREQUISITES

### A. Must know before starting
| Topic | Why it matters | Depth needed | Self-test |
|---|---|---|---|
| Basic computer literacy | You'll live in a terminal and a code editor | Comfortable installing software, navigating folders | Can you install VS Code and a Linux VM without help? |
| Basic typing/terminal comfort | Speed and comfort reduce friction | Not fear the command line | Can you open a terminal and run `ls`, `cd`, `pwd` without googling? |
| Basic logical thinking / any programming exposure | DevOps = scripting + systems logic | If/else, loops, variables in ANY language | Can you write a simple script (any language) that loops and checks a condition? |

### B. Can learn during the roadmap (built into Month 1)
- Linux fundamentals
- Networking basics (OSI, TCP/IP, DNS, ports)
- Git/GitHub
- Bash scripting
- JSON/YAML syntax
- Basic Python (helpful, not mandatory — Bash is prioritized)

### C. Nice to have (not required)
- Prior sysadmin experience
- Existing AWS account experience
- Prior exposure to Docker
- CS degree / formal networking course

### Depth check for each core prerequisite

| Prerequisite | Why it matters | How much you need | How to test yourself |
|---|---|---|---|
| Linux basics | Nearly all DevOps tooling runs on Linux | Navigate filesystem, manage processes, edit files via CLI | Set up a Linux VM and survive a day without a GUI file manager |
| HTTP/HTTPS | Everything you deploy is served over these | Understand request/response, status codes, headers | Explain what happens when you type a URL and hit Enter |
| DNS | You'll debug "site not resolving" issues constantly | What a DNS record is, how resolution works | Explain the difference between an A record and a CNAME |
| IP addresses / ports | Needed for networking, firewalls, security groups | Public vs private IP, common ports (22, 80, 443, 3306, etc.) | List 5 common ports and their services from memory |
| TCP/IP | Underlies containers, Kubernetes networking, cloud VPCs | Conceptual understanding of packets, connections | Explain TCP handshake in your own words |
| SSH | You'll SSH into servers daily | Key-based auth, basic SSH config | SSH into a remote VM using a key pair, not a password |
| Git/GitHub | Every project and CI/CD pipeline depends on it | Commit, branch, merge, push, pull, resolve conflicts | Resolve a merge conflict without panicking |
| Basic Bash | Automation glue for almost every DevOps task | Variables, loops, conditionals, exit codes | Write a script that checks if a file exists and reacts accordingly |
| JSON/YAML | Config format for Docker, Kubernetes, CI/CD, Terraform | Read and hand-write both correctly | Convert a small JSON object to YAML by hand |
| Basic cloud concepts | Foundation for AWS module | What "the cloud" actually is (someone else's servers + APIs) | Explain the difference between IaaS, PaaS, SaaS |

---

## 3. DEVOPS SKILL TREE

```
DEVOPS
├── Linux — filesystem, permissions, processes, services, package mgmt, logs, SSH
├── Networking — OSI/TCP-IP, DNS, ports, HTTP/HTTPS, load balancing, firewalls
├── Git — commits, branching, merging, PRs, conflict resolution, history
├── Bash — variables, control flow, functions, automation scripts
├── Python (light) — scripting for tooling, reading automation scripts
├── Docker — images, containers, volumes, networking, Compose
├── CI/CD — pipelines, stages, artifacts, secrets, deployment strategies
├── Cloud (AWS) — EC2, S3, VPC, IAM, ECR, CloudWatch
├── Infrastructure as Code — Terraform providers/resources/state/modules
├── Kubernetes — pods, deployments, services, config, ingress, scaling
├── Monitoring — Prometheus metrics/alerts, Grafana dashboards
├── Logging — centralized logs, log levels, correlation
├── Security — least privilege, secrets mgmt, scanning, network security
├── DevSecOps — shifting security left, pipeline scanning
├── SRE — SLIs/SLOs, incident response, postmortems
├── Troubleshooting — systematic diagnosis across the stack
├── Automation — scripting recurring tasks out of existence
├── AI-assisted DevOps — using AI as a force multiplier, safely
└── Production practices — rollbacks, blue/green, on-call hygiene, documentation
```

For each category below: **Beginner level** = what you must master in 3 months. **Intermediate** = what you'll grow into later. **Don't learn yet** = explicitly deferred.

| Category | Beginner level (this roadmap) | Intermediate (later) | Don't learn yet | Job relevance |
|---|---|---|---|---|
| Linux | Filesystem, permissions, processes, services, SSH, logs | Kernel tuning, custom systemd units, performance profiling | Kernel compilation | Very high |
| Networking | OSI/TCP-IP basics, DNS, ports, HTTP(S), firewalls, LB concept | BGP, advanced routing, service mesh networking | Deep routing protocols | Very high |
| Git | Branch/merge/PR/conflicts | Rebase strategies, git internals, monorepo tooling | Custom git hooks at scale | Very high |
| Bash | Variables, loops, functions, exit codes | Advanced text processing (awk/sed mastery) | Writing entire apps in Bash | High |
| Docker | Images, containers, volumes, Compose | Multi-stage builds, custom base image hardening | Building a container runtime | Very high |
| CI/CD | GitHub Actions pipelines, secrets, artifacts | Matrix builds, reusable workflows, multi-env promotion | Mastering 4 different CI tools | Very high |
| AWS | EC2, S3, VPC, IAM, ECR, CloudWatch | RDS, Lambda, multi-account setups | All 200+ AWS services | Very high |
| Terraform | Resources, variables, state, modules | Remote state locking at scale, Terraform Cloud | Writing custom providers | High |
| Kubernetes | Pods, deployments, services, config, ingress, scaling basics | Operators, CRDs, service mesh, multi-cluster | Building your own K8s distro | High (growing) |
| Monitoring | Prometheus scraping/alerts, Grafana dashboards | Long-term storage, federation, SLO burn-rate alerts | Full observability platform design | High |
| Security | Least privilege, secrets, image scanning basics | Full DevSecOps pipeline, compliance frameworks | Advanced pentesting | High |
| SRE | Incident response basics, postmortems | Error budgets, chaos engineering | Building your own SRE platform | Medium (growing) |

---

## 4–5. THE 12-WEEK ROADMAP + DAILY SCHEDULE SYSTEM

### Repeatable weekday structure (3 hrs)
- **Block 1 (45 min) — Learning:** read/watch the concept, take notes in your own words
- **Block 2 (90 min) — Hands-on:** labs, exercises, building
- **Block 3 (30 min) — Documentation:** write what you did, what broke, what you learned
- **Block 4 (15 min) — Revision:** flashcards/quick recall of yesterday's topic

*(Adjust ratios when a topic is more conceptual — e.g., Networking Week 2 might be 60/60/30/15 — hands-on always gets the largest or equal share.)*

### Weekend structure (4 hrs each day = 8 hrs/weekend)
- 2 hrs project work
- 2 hrs troubleshooting drills / revision
- 2 hrs interview question practice
- 1 hr documentation / GitHub README polishing
- 1 hr architecture review / reading

---

### WEEK 1 — Linux Foundations I

**Main objective:** Get comfortable living in Linux via terminal only.
**Skills learned:** Filesystem navigation, permissions, users/groups, package management.
**Topics/Subtopics:** Linux architecture (kernel/shell), filesystem hierarchy, `ls/cd/pwd/cp/mv/rm`, file permissions (rwx, chmod, chown), users & groups, package managers (apt/yum).
**Theory:** 4 hrs | **Hands-on:** 9 hrs | **Revision:** 2 hrs | **AI-assisted:** 2 hrs | **Interview prep:** 1 hr
**Weekly deliverable:** A personal Linux "cheat sheet" repo on GitHub documenting every command learned with your own examples.
**GitHub activity:** Create `linux-notes` repo, commit daily.
**Checkpoint:** Can you create a folder structure, set specific permissions on files for different users, and explain why, without notes?
**Should be able to explain:** Difference between a file owner, group, and others; what `chmod 755` means.
**Should be able to build:** A directory structure with correct permission levels for a mock multi-user project.
**Common mistakes:** Using `chmod 777` to "make it work"; confusing `sudo` with owning a file.
**Troubleshooting exercise:** Given a "Permission denied" error, diagnose and fix it using only `ls -l`, `whoami`, and `chmod/chown`.

**Daily plan:**
- Mon: Linux architecture + filesystem hierarchy → hands-on navigation drills
- Tue: File operations (create/copy/move/delete) → build a nested folder structure
- Wed: Permissions & ownership → permission puzzles (given a scenario, set correct permissions)
- Thu: Users & groups → create users/groups on your VM, assign permissions
- Fri: Package management (apt/yum) → install/remove/update packages, explore `/var/log`
- Sat (4h): Review all week's commands hands-on + write cheat sheet + 1 troubleshooting scenario
- Sun (4h): Redo hardest exercises from memory + 10 interview questions (Linux basics) + document learnings

---

### WEEK 2 — Linux Foundations II + Networking Basics

**Main objective:** Master processes/services and understand how machines talk to each other.
**Skills learned:** Process management, systemd services, environment variables, log inspection, OSI/TCP-IP fundamentals, DNS.
**Topics:** `ps/top/htop`, `kill/systemctl`, environment variables, `/var/log`, journalctl, OSI model, TCP/IP, DNS resolution, ports.
**Theory:** 5 hrs | **Hands-on:** 8 hrs | **Revision:** 2 hrs | **AI-assisted:** 2 hrs | **Interview prep:** 1 hr
**Weekly deliverable:** Diagram (drawn by hand or in a tool) of the OSI model with real-world analogies added by you.
**GitHub activity:** Add networking notes to `linux-notes` repo (rename to `foundations-notes` if you like).
**Checkpoint:** Can you find and kill a runaway process, then read logs to understand what happened?
**Should be able to explain:** What a systemd service is; the layers of OSI/TCP-IP; how DNS resolves a domain.
**Should be able to build:** A running background service (a simple long-running script) managed with systemd, that you can start/stop/check status of.
**Common mistakes:** Killing processes with `kill -9` as a first resort; skipping log inspection before asking for help.
**Troubleshooting exercise:** A service "isn't working" — diagnose via `systemctl status`, `journalctl`, and process list.

**Daily plan:**
- Mon: Process management (`ps`, `top`, `kill`) → find & terminate specific processes
- Tue: systemd services → create and manage a simple custom service
- Wed: Environment variables & logs → configure env vars, tail logs
- Thu: OSI model + TCP/IP theory → map real actions (browsing) to OSI layers
- Fri: DNS + ports → use `dig`/`nslookup`, list common ports and services
- Sat (4h): Build a small "systemd service" lab + document + 1 troubleshooting scenario
- Sun (4h): Networking quiz (self-made) + 10 interview Qs (Linux + networking) + revise Week 1–2

---

### WEEK 3 — Networking Deep Dive + SSH + Git Basics

**Main objective:** Understand HTTP(S), remote access, and version control fundamentals.
**Skills:** HTTP/HTTPS/TLS basics, reverse proxy & load balancer concepts, firewalls, SSH key auth, Git init/commit/branch.
**Topics:** HTTP methods & status codes, TLS handshake concept, reverse proxy vs load balancer, firewall rules concept, SSH keygen & config, Git basics (init, add, commit, log, branch).
**Theory:** 5 hrs | **Hands-on:** 8 hrs | **Revision:** 2 hrs | **AI-assisted:** 2 hrs | **Interview prep:** 1 hr
**Weekly deliverable:** A "networking + git glossary" doc with your own plain-English definitions.
**GitHub activity:** First real Git workflow practice — multiple branches, at least one merge, one intentional conflict resolved.
**Checkpoint:** Can you SSH into a remote VM using key-based auth only (password auth disabled)?
**Should be able to explain:** Difference between reverse proxy and load balancer; HTTP vs HTTPS; what a firewall rule does.
**Should be able to build:** A hardened SSH setup (key-only login) on a cloud VM or local VM.
**Common mistakes:** Leaving password SSH auth enabled; committing directly to `main` without branches.
**Troubleshooting exercise:** SSH connection refused — diagnose (service running? firewall? correct key? correct port?).

**Daily plan:**
- Mon: HTTP/HTTPS deep dive → inspect real requests/responses (browser dev tools)
- Tue: TLS basics + reverse proxy/load balancer concepts → diagram both
- Wed: Firewalls & security groups (concept only) → design rules for a mock 3-tier app
- Thu: SSH keygen, config, hardening → set up key-only SSH to a VM
- Fri: Git fundamentals → init repo, commits, branches, log
- Sat (4h): Git branching/merging practice + create and resolve a real conflict
- Sun (4h): Full networking+SSH+git review + 15 interview Qs + document week

---

### WEEK 4 — Bash Scripting + Docker Introduction

**Main objective:** Automate simple tasks with Bash; understand what containers are and why they exist.
**Skills:** Bash variables/conditionals/loops/functions, Docker images vs containers, basic Dockerfile concepts.
**Topics:** Bash scripting fundamentals, exit codes, arguments, Docker architecture (engine, image, container, registry), Dockerfile instructions (conceptual), container lifecycle.
**Theory:** 5 hrs | **Hands-on:** 9 hrs | **Revision:** 2 hrs | **AI-assisted:** 2 hrs | **Interview prep:** 1 hr
**Weekly deliverable:** A Bash script that automates a real repetitive task on your machine (e.g., backup a folder, clean logs). A written (not copied) Dockerfile for a simple app you choose.
**GitHub activity:** New repo `bash-automation-scripts`; commit script with a README explaining what/why.
**Checkpoint:** Can you explain, without help, the difference between an image and a container?
**Should be able to explain:** Why containers solve "works on my machine"; Docker image layering concept.
**Should be able to build:** A working Docker image for a simple app you containerize yourself, and run it as a container with port mapping.
**Common mistakes:** Treating containers like VMs (installing an OS' worth of stuff inside); forgetting `.dockerignore`.
**Troubleshooting exercise:** Container exits immediately after `docker run` — diagnose using `docker logs`, `docker inspect`.

**Daily plan:**
- Mon: Bash variables, conditionals → write scripts with if/else logic
- Tue: Bash loops, functions, arguments → build a multi-function utility script
- Wed: Exit codes & automation patterns → chain scripts, handle failures
- Thu: Docker architecture & image concepts → pull/run existing images, inspect them
- Fri: Dockerfile concepts (layers, instructions) → write your first Dockerfile from scratch
- Sat (4h): Build/run/debug your own containerized app + 1 troubleshooting scenario
- Sun (4h): Docker networking & volumes intro + review week + 15 interview Qs (Bash + Docker)

**[END OF MONTH 1 CHECKPOINT]** — You should now be able to: navigate Linux confidently, explain core networking, use Git for real workflows, write basic Bash automation, and containerize a simple application.

---

### WEEK 5 — Docker Deep Dive + Docker Compose

**Main objective:** Move from "single container" to "multi-container systems."
**Skills:** Volumes, Docker networking, Docker Compose, container troubleshooting.
**Topics:** Named volumes vs bind mounts, container networking modes, Compose file structure (conceptual), multi-service orchestration on one host.
**Theory:** 4 hrs | **Hands-on:** 10 hrs | **Revision:** 2 hrs | **AI-assisted:** 2 hrs | **Interview prep:** 1 hr
**Weekly deliverable:** A multi-container app (e.g., app + database) running via Docker Compose that you designed and wrote yourself.
**GitHub activity:** New repo `multi-container-app`; full README with architecture explanation.
**Checkpoint:** Can two containers you built talk to each other over a Docker network, with data persisted via a volume?
**Should be able to explain:** Why data is lost without volumes; bridge vs host networking.
**Should be able to build:** A 2–3 service Compose stack (e.g., app + db + cache) from scratch.
**Common mistakes:** Hardcoding IPs instead of using service names; not persisting database data.
**Troubleshooting exercise:** App container can't reach database container — diagnose network config.

**Daily plan:**
- Mon: Volumes (named vs bind mounts) → persist data across container restarts
- Tue: Docker networking modes → connect two containers manually (no Compose yet)
- Wed: Docker Compose structure & concepts → convert your manual setup to Compose
- Thu: Multi-service design → add a 3rd service (cache/queue)
- Fri: Container troubleshooting patterns → intentionally break your stack, fix it
- Sat (4h): Finish + document multi-container project + push to GitHub
- Sun (4h): 5 Docker troubleshooting scenarios (self-created) + 15 interview Qs

---

### WEEK 6 — CI/CD Foundations with GitHub Actions

**Main objective:** Understand CI/CD conceptually and build your first working pipeline.
**Skills:** CI/CD concepts, GitHub Actions structure (workflows, jobs, steps), secrets, artifacts.
**Topics:** CI vs CD, pipeline stages, runners, triggers, secrets management, build artifacts, basic deployment strategies (conceptual).
**Theory:** 5 hrs | **Hands-on:** 9 hrs | **Revision:** 2 hrs | **AI-assisted:** 2 hrs | **Interview prep:** 1 hr
**Weekly deliverable:** A GitHub Actions pipeline that runs tests and builds a Docker image automatically on push.
**GitHub activity:** Add `.github/workflows` to your Project 1 repo (start it now if not started).
**Checkpoint:** Does your pipeline turn green automatically when you push code, and red when you break a test on purpose?
**Should be able to explain:** Difference between CI and CD; what a "runner" is; why secrets shouldn't be hardcoded.
**Should be able to build:** A pipeline: push → install deps → run tests → build Docker image.
**Common mistakes:** Committing secrets directly into workflow files; pipelines with no failure notifications.
**Troubleshooting exercise:** Pipeline fails only in CI, not locally — diagnose environment differences.

**Daily plan:**
- Mon: CI/CD concepts (why it exists, CI vs CD) → map your own mental model
- Tue: GitHub Actions structure (workflows/jobs/steps/triggers) → write a "hello world" workflow
- Wed: Secrets & environment variables in Actions → securely use a secret in a workflow
- Thu: Build & test stage → run automated tests on push
- Fri: Docker build stage → build and tag an image inside the pipeline
- Sat (4h): Full pipeline integration (test → build → tag) + break it intentionally, fix it
- Sun (4h): Jenkins conceptual overview (no hands-on) + 15 interview Qs (CI/CD)

---

### WEEK 7 — AWS Foundations I (Compute, Storage, IAM)

**Main objective:** Get comfortable in the AWS console/CLI and understand core building blocks.
**Skills:** EC2, S3, IAM users/roles/policies, least privilege principle.
**Topics:** EC2 instance lifecycle, security groups, S3 buckets & policies, IAM users vs roles, least-privilege design.
**Theory:** 6 hrs | **Hands-on:** 8 hrs | **Revision:** 2 hrs | **AI-assisted:** 2 hrs | **Interview prep:** 1 hr
**Weekly deliverable:** A running EC2 instance you provisioned, secured, and SSH'd into, plus an S3 bucket with a correctly scoped IAM policy (not `*` on everything).
**GitHub activity:** New repo `aws-notes`; document every service with your own diagrams.
**Checkpoint:** Can you explain why you should never use your root AWS account for daily work?
**Should be able to explain:** IAM least privilege; difference between a user and a role; what a security group actually is.
**Should be able to build:** An EC2 instance with a correctly scoped security group, accessible only via SSH from your IP.
**Common mistakes:** Using root credentials for everything; overly permissive security groups (0.0.0.0/0 on all ports).
**Troubleshooting exercise:** Can't SSH into EC2 instance — diagnose (security group? key pair? instance state?).

**Daily plan:**
- Mon: AWS account setup, IAM fundamentals (users, groups, policies) → create a non-root IAM user
- Tue: IAM roles & least privilege → design a policy for a specific task only
- Wed: EC2 basics (instance types, AMIs, key pairs) → launch your first instance
- Thu: Security groups → configure inbound/outbound rules correctly
- Fri: S3 basics → create buckets, set policies, upload/download objects
- Sat (4h): Build a small "static website on S3 + EC2 app" mini-lab
- Sun (4h): AWS troubleshooting scenarios + 20 interview Qs (AWS basics)

---

### WEEK 8 — AWS Foundations II (Networking) + ECR + CloudWatch

**Main objective:** Understand how AWS networking ties everything together; push images to a registry.
**Skills:** VPC, subnets, route tables, Internet Gateway, NAT concept, ECR, CloudWatch basics.
**Topics:** VPC design (public/private subnets), route tables, IGW vs NAT gateway, ECR push/pull, CloudWatch logs & basic metrics/alarms.
**Theory:** 6 hrs | **Hands-on:** 8 hrs | **Revision:** 2 hrs | **AI-assisted:** 2 hrs | **Interview prep:** 1 hr
**Weekly deliverable:** A custom VPC (public + private subnet) hosting your EC2 instance, plus your Docker image pushed to ECR, plus a CloudWatch alarm.
**GitHub activity:** Expand `aws-notes` with VPC architecture diagrams.
**Checkpoint:** Can you explain why a private subnet has no direct internet access, and how a NAT gateway changes that?
**Should be able to explain:** Public vs private subnet; what a route table does; why you'd use ECR over Docker Hub in AWS workflows.
**Should be able to build:** A VPC with correctly routed public/private subnets, an EC2 instance in the public subnet, an image in ECR, and a CloudWatch alarm on CPU usage.
**Common mistakes:** Putting everything in one subnet with no segmentation; ignoring CloudWatch until something breaks.
**Troubleshooting exercise:** EC2 in private subnet can't reach the internet for updates — diagnose route table/NAT config.

**Daily plan:**
- Mon: VPC fundamentals (CIDR, subnets) → design your own VPC on paper first
- Tue: Route tables, IGW → build the public subnet, verify internet access
- Wed: NAT gateway concept + private subnet → build the private subnet
- Thu: ECR → push your Week 4–5 Docker image to your own ECR repo
- Fri: CloudWatch → set up logs and a basic CPU/metric alarm
- Sat (4h): Full VPC + EC2 + ECR integration lab, document architecture
- Sun (4h): 20 interview Qs (AWS networking) + revise Weeks 7–8 + troubleshooting drills

**[END OF MONTH 2, PART A CHECKPOINT]**

---

### WEEK 9 — Terraform Foundations

**Main objective:** Recreate what you built manually in AWS — but as code.
**Skills:** IaC principles, Terraform providers/resources/variables/outputs, state, plan/apply/destroy.
**Topics:** Why IaC matters, Terraform architecture, HCL basics (conceptually, no full code given to you), state file purpose, resource dependency graph.
**Theory:** 6 hrs | **Hands-on:** 8 hrs | **Revision:** 2 hrs | **AI-assisted:** 2 hrs | **Interview prep:** 1 hr
**Weekly deliverable:** Your Week 7–8 AWS setup (VPC + EC2 + security group) recreated entirely with Terraform, written by you.
**GitHub activity:** New repo `terraform-aws-infra`; document `plan`/`apply`/`destroy` outputs in README.
**Checkpoint:** Can you `terraform destroy` your infra and `terraform apply` it back identically?
**Should be able to explain:** Why state matters; what happens if two people apply Terraform at once without remote state; declarative vs imperative IaC.
**Should be able to build:** A working Terraform config that provisions VPC + subnet + EC2 + security group, using variables (not hardcoded values).
**Common mistakes:** Manually editing infra that Terraform manages (drift); committing `.tfstate` with secrets to a public repo.
**Troubleshooting exercise:** `terraform apply` fails midway — diagnose using plan output and state inspection.

**Daily plan:**
- Mon: Why IaC? Terraform architecture, providers → install Terraform, initialize a project
- Tue: Resources & variables → define your first resource (e.g., a security group)
- Wed: State concept (why it exists, risks of local state) → inspect your local state file
- Thu: Outputs & dependency management → chain resources together (VPC → subnet → EC2)
- Fri: Plan/Apply/Destroy workflow → full apply/destroy cycle, multiple times
- Sat (4h): Rebuild your entire Week 7–8 AWS lab in Terraform end-to-end
- Sun (4h): 20 interview Qs (Terraform) + document + troubleshooting drills

---

### WEEK 10 — Terraform Modules + Project 1 & 2 Completion

**Main objective:** Make your infrastructure reusable; finish your first two portfolio projects.
**Skills:** Modules, remote state concept, environment separation, reusable infra design.
**Topics:** Module structure, input/output variables for modules, remote state (S3 backend concept), workspaces (conceptual), environment separation (dev/prod pattern).
**Theory:** 4 hrs | **Hands-on:** 10 hrs | **Revision:** 2 hrs | **AI-assisted:** 2 hrs | **Interview prep:** 1 hr
**Weekly deliverable:** Project 1 (CI/CD pipeline) and Project 2 (Terraform infra) fully complete, documented, and pushed to GitHub with proper READMEs.
**GitHub activity:** Finalize `terraform-aws-infra` with a module structure; finalize CI/CD project repo.
**Checkpoint:** Could a stranger clone your Terraform repo and deploy the same infra by reading only your README?
**Should be able to explain:** Why modules improve maintainability; the tradeoffs of local vs remote state.
**Should be able to build:** A reusable Terraform module (e.g., a "network" module) called from a root config with different variable inputs.
**Common mistakes:** Overengineering modules too early; skipping documentation because "the code is self-explanatory" (it never is to a stranger).
**Troubleshooting exercise:** Module produces unexpected resource because of a variable default — diagnose and fix.

**Daily plan:**
- Mon: Module structure & design → refactor Week 9's config into a module
- Tue: Module variables/outputs → parametrize your module properly
- Wed: Remote state concept (S3 backend) → research and document how it would work (setup if time allows)
- Thu: Project 1 polish (CI/CD) → finalize pipeline, write full README
- Fri: Project 2 polish (Terraform) → finalize infra, write full README + architecture diagram
- Sat (4h): Full project 1 + 2 review, record yourself explaining both out loud
- Sun (4h): 20 interview Qs (mixed AWS/Terraform/CI-CD) + fix any repo gaps

---

### WEEK 11 — Kubernetes Foundations I

**Main objective:** Understand Kubernetes architecture and deploy your first app to a cluster.
**Skills:** K8s architecture, pods, deployments, services, namespaces, ConfigMaps/Secrets.
**Topics:** Control plane vs worker nodes, pod lifecycle, deployments & ReplicaSets, services (ClusterIP/NodePort/LoadBalancer concept), namespaces, ConfigMaps & Secrets.
**Theory:** 6 hrs | **Hands-on:** 8 hrs | **Revision:** 2 hrs | **AI-assisted:** 2 hrs | **Interview prep:** 1 hr
**Weekly deliverable:** Your containerized app from Month 1 deployed to a local Kubernetes cluster (minikube/kind) with a Service exposing it.
**GitHub activity:** New repo `k8s-deployment-lab`; document YAML structure decisions (write your own, don't copy).
**Checkpoint:** Can you scale your deployment to 3 replicas and explain what Kubernetes does behind the scenes?
**Should be able to explain:** Why Kubernetes uses declarative desired-state management; pod vs deployment vs ReplicaSet.
**Should be able to build:** A Deployment + Service + ConfigMap for your app, running locally on minikube/kind.
**Common mistakes:** Editing pods directly instead of deployments; hardcoding config instead of using ConfigMaps.
**Troubleshooting exercise:** Pod stuck in `Pending` — diagnose using `kubectl describe`.

**Daily plan:**
- Mon: K8s architecture (control plane, nodes, kubelet) → set up minikube/kind
- Tue: Pods & Deployments → deploy your first pod, then a deployment
- Wed: Services (ClusterIP/NodePort) → expose your deployment
- Thu: Namespaces + ConfigMaps → organize resources, externalize config
- Fri: Secrets → move sensitive config into a Secret properly
- Sat (4h): Full app deployment end-to-end (Deployment + Service + ConfigMap + Secret)
- Sun (4h): 20 interview Qs (Kubernetes basics) + troubleshooting drills

---

### WEEK 12 — Kubernetes II + Monitoring + Final Project Polish

**Main objective:** Add resilience (health checks, rolling updates), observability, and finish all 4 projects.
**Skills:** Ingress, health checks, rolling updates/rollback, scaling, Prometheus/Grafana basics, DevSecOps basics.
**Topics:** Liveness/readiness probes, rolling deployment strategy & rollback, HPA concept, Ingress basics, Prometheus scraping/PromQL basics, Grafana dashboards, monitoring vs logging vs tracing.
**Theory:** 6 hrs | **Hands-on:** 8 hrs | **Revision:** 2 hrs | **AI-assisted:** 2 hrs | **Interview prep:** 2 hrs
**Weekly deliverable:** All 4 portfolio projects complete, documented, and polished. Project 3 (Kubernetes) and Project 4 (Observability) finished this week.
**GitHub activity:** Final polish pass across ALL repos — READMEs, diagrams, screenshots, "lessons learned" sections.
**Checkpoint:** Can you cause a deliberate pod failure, watch it self-heal or alert, and explain the full chain of events?
**Should be able to explain:** Rolling update vs recreate strategy; what a liveness probe protects against; PromQL basics; monitoring vs logging vs tracing vs observability.
**Should be able to build:** A K8s deployment with health checks and a working rolling update/rollback; a Grafana dashboard fed by Prometheus metrics with at least one alert rule.
**Common mistakes:** No health checks (K8s can't tell if your app is actually broken); dashboards with no alerts (nobody's watching).
**Troubleshooting exercise:** `CrashLoopBackOff` on rollout — diagnose root cause and roll back safely.

**Daily plan:**
- Mon: Health checks (liveness/readiness) → add probes, test failure behavior
- Tue: Rolling updates & rollback → deploy a broken version, roll back
- Wed: Prometheus basics (scraping, exporters, PromQL) → scrape a metric from your app
- Thu: Grafana basics → build a dashboard from your Prometheus data + 1 alert
- Fri: Monitoring vs logging vs tracing vs observability (theory) + Ingress basics
- Sat (4h): Finish Project 3 (Kubernetes) fully — failures, diagnosis, documentation
- Sun (4h): Finish Project 4 (Observability) fully — dashboards, alerts, postmortem doc

**[END OF ROADMAP CHECKPOINT]** — All 4 projects complete. Move into full mock-interview and job-application mode (see Parts 12–15).

---

## 9. AI FOR DEVOPS

**Core principle: AI is an assistant, not a replacement for DevOps fundamentals.** If you can't explain *why* a fix works, you don't actually know it — you just have a working paste.

### How AI helps your learning
- Explaining confusing Linux/networking/Kubernetes errors in plain language
- Generating practice questions and mock interview scenarios
- Helping you build/adjust study plans as you discover gaps
- Explaining *why* something works, not just *what* to type

### How to use AI for troubleshooting (structured prompt pattern)
Give the AI:
1. The exact error message
2. Relevant logs (sanitized — see below)
3. Environment description (OS, tool versions, cloud/local)
4. What changed recently
5. Expected behavior
6. Actual behavior

Then ask it to:
1. Explain the problem in plain language
2. List possible causes
3. Rank the causes by likelihood
4. Suggest diagnostic commands (not fixes yet)
5. Explain what each diagnostic command's output would mean
6. Only then suggest remediation
7. Explain the risk of each proposed fix

**You must still run the diagnostics yourself and verify results before applying any fix.** AI can be confidently wrong.

### Practical AI usage across daily DevOps work
Log analysis · incident investigation · explaining unfamiliar shell commands · Terraform plan/error interpretation · Kubernetes error diagnosis · CI/CD failure analysis · writing documentation drafts · runbook drafting · architecture brainstorming (not final decisions) · drafting PromQL/monitoring queries · summarizing incidents · a "second pair of eyes" on pull requests · security review checklists · generating test case ideas · release note drafting · postmortem structuring.

### AI safety rules — never paste into a public AI tool:
- Passwords, API keys, AWS credentials, private/SSH keys
- Customer data or PII
- Production secrets or `.env` files as-is
- Confidential company information
- Raw sensitive logs

**Sanitize logs before pasting:** strip IPs, hostnames, account IDs, tokens, usernames, and replace with placeholders like `<IP>`, `<ACCOUNT_ID>`, `<TOKEN>` while keeping the error structure intact.

### AI for interview preparation
Use AI to simulate: Linux, AWS, Docker, Kubernetes, Terraform, troubleshooting, and behavioral interviews. **Rule:** answer the question yourself first, out loud or in writing, *then* ask AI to critique your answer — never ask AI to answer first and memorize its response.

---

## 10. FOUR PORTFOLIO PROJECTS

### Project difficulty ranking & order
| Project | Difficulty | Build order |
|---|---|---|
| 1. Automated Application Delivery Platform | Beginner → Intermediate | **1st** — builds core CI/CD muscle |
| 2. Infrastructure as Code Cloud Platform | Intermediate | **2nd** — builds on AWS knowledge from Project 1's deployment target |
| 3. Kubernetes Production-Like Platform | Intermediate → Advanced | **3rd** — needs containers (P1) and infra concepts (P2) |
| 4. Observability + Self-Healing Platform | Advanced | **4th** — needs a running app (P1/P3) to actually monitor |

**Why this order:** Each project's output becomes an input to the next. Project 1 gives you a containerized, pipeline-deployed app. Project 2 gives you the cloud infrastructure to host it properly. Project 3 puts it on Kubernetes. Project 4 observes and hardens what you built. Building them in this sequence also means your GitHub tells a coherent growth story instead of four disconnected exercises.

---

### PROJECT 1 — Automated Application Delivery Platform

- **Real-world problem:** Manual deployments are slow and error-prone; teams need push-to-deploy automation.
- **Business scenario:** A small startup needs their app auto-tested, built, and deployed on every merge to main, without a human manually SSH-ing into servers.
- **Architecture:** Git push → GitHub Actions triggers → automated tests → Docker build → push to ECR → deploy (to EC2 or equivalent).
- **Technologies:** GitHub, GitHub Actions, Docker, AWS, ECR.
- **Skills demonstrated:** CI/CD pipeline design, containerization, cloud registry usage, automated testing integration.
- **Infrastructure:** A single EC2 instance (or container host) as the deployment target.
- **CI/CD:** Multi-stage pipeline (test → build → push → deploy) with secrets managed via GitHub Secrets.
- **Security:** No hardcoded credentials; scoped IAM permissions for the deployment; `.dockerignore` used correctly.
- **Monitoring:** Basic — pipeline status badges, deployment logs.
- **Failure scenarios to simulate:** failing test blocks deployment; bad image tag; expired/invalid AWS credentials in pipeline.
- **Troubleshooting scenarios:** pipeline succeeds but app isn't updated (caching issue); pipeline fails only in CI, not locally.
- **Expected repo structure:** `/app`, `/.github/workflows`, `Dockerfile`, `README.md`, `docs/architecture.png`.
- **README requirements:** problem statement, architecture diagram, how to run locally, how the pipeline works, what happens on failure.
- **Architecture diagram requirements:** show every stage from git push to running container, including where secrets are used.
- **Resume bullet points (examples, not templates to copy verbatim):**
  - "Designed and built an automated CI/CD pipeline using GitHub Actions that tests, containerizes, and deploys an application to AWS on every push to main."
  - "Implemented secrets management and least-privilege IAM roles for a fully automated deployment workflow."
- **Interview questions:** "Walk me through what happens from the moment you `git push` to the app being live." "What happens if the test stage fails — does anything deploy?" "How are your AWS credentials protected in this pipeline?"
- **Possible improvements:** add staging vs production environments; add manual approval gate before production deploy; add rollback step.

---

### PROJECT 2 — Infrastructure as Code Cloud Platform

- **Real-world problem:** Manually clicking through AWS console doesn't scale and isn't reproducible or auditable.
- **Business scenario:** A company needs infrastructure that can be recreated identically in a new AWS account/region within minutes, and destroyed cleanly when no longer needed.
- **Architecture:** VPC with public/private subnets → EC2 in public subnet → S3 for storage → IAM roles scoped per resource → CloudWatch for basic monitoring.
- **Technologies:** Terraform, AWS (VPC, EC2, S3, IAM, CloudWatch).
- **Skills demonstrated:** Infrastructure as Code, modular design, state management understanding, reproducible infra.
- **Infrastructure:** Full networking stack + compute + storage, defined entirely in Terraform.
- **CI/CD:** Optional stretch — a pipeline that runs `terraform plan` on PR and `apply` on merge (only attempt if time allows).
- **Security:** IAM least privilege per resource; no `0.0.0.0/0` on sensitive ports; state file never committed with secrets.
- **Monitoring:** CloudWatch alarm on at least one metric (e.g., CPU).
- **Failure scenarios:** apply fails halfway through (partial state); wrong CIDR range causes subnet conflict.
- **Troubleshooting scenarios:** resource drift (someone manually changed something in console); state lock issues.
- **Expected repo structure:** `/modules/network`, `/modules/compute`, root `main.tf`/`variables.tf`/`outputs.tf`, `README.md`, `docs/architecture.png`.
- **README requirements:** architecture diagram, prerequisites, how to `init/plan/apply/destroy`, module explanation, variable reference table.
- **Architecture diagram requirements:** full VPC layout — subnets, route tables, gateway, where each resource lives.
- **Resume bullet points (examples):**
  - "Built reusable, modular Terraform infrastructure provisioning a full AWS VPC, compute, and storage layer with environment-based variable separation."
  - "Implemented least-privilege IAM policies across all provisioned AWS resources."
- **Interview questions:** "Why did you split this into modules instead of one file?" "What happens to your data if you run `terraform destroy` right now?" "How would you handle two engineers running `apply` at the same time?"
- **Possible improvements:** add remote state with locking; add a second environment (staging) using the same modules with different variables.

---

### PROJECT 3 — Kubernetes Production-Like Platform

- **Real-world problem:** Running containers on a single host doesn't scale or self-heal; teams need orchestration.
- **Business scenario:** The startup's app has grown — they need it to auto-restart on crash, scale under load, and support zero-downtime updates.
- **Architecture:** Deployment + Service + Ingress + ConfigMap + Secret + PersistentVolumeClaim, running on minikube/kind (or a managed cluster if accessible).
- **Technologies:** Kubernetes, kubectl, your Project 1 Docker image.
- **Skills demonstrated:** Container orchestration, self-healing systems design, rolling deployments, K8s troubleshooting.
- **Infrastructure:** Local cluster (minikube/kind) is sufficient and expected for a learning project.
- **CI/CD:** Optional stretch — extend Project 1's pipeline to `kubectl apply` on deploy.
- **Security:** Secrets stored as K8s Secrets, not ConfigMaps; no hardcoded credentials in manifests.
- **Monitoring:** Basic health checks (liveness/readiness probes) — full monitoring lives in Project 4.
- **Failure scenarios to intentionally create:** broken image tag, misconfigured ConfigMap reference, wrong Service selector, insufficient resource requests causing scheduling failure, bad Ingress path.
- **Troubleshooting scenarios:** `CrashLoopBackOff`, `ImagePullBackOff`, pod `Pending` forever, Service returns connection refused.
- **Expected repo structure:** `/manifests` (deployment.yaml, service.yaml, configmap.yaml, secret.yaml, ingress.yaml), `README.md`, `docs/failure-scenarios.md`.
- **README requirements:** architecture diagram, how to deploy locally, a dedicated "failure scenarios I diagnosed" section with root cause + fix for each.
- **Architecture diagram requirements:** show pod/deployment/service/ingress relationships and data flow.
- **Resume bullet points (examples):**
  - "Deployed and managed a containerized application on Kubernetes with rolling updates, health checks, and self-healing configuration."
  - "Diagnosed and documented 6+ Kubernetes failure scenarios including CrashLoopBackOff and networking misconfigurations."
- **Interview questions:** "Your pod is stuck in CrashLoopBackOff — walk me through your diagnosis." "What's the difference between a liveness and readiness probe, and what happens if you get it backwards?" "How does Kubernetes decide which node to schedule a pod on?"
- **Possible improvements:** add HorizontalPodAutoscaler; add PersistentVolume for stateful data; migrate to a real managed cluster (EKS) as a stretch goal.

---

### PROJECT 4 — Observability + Self-Healing DevOps Platform

- **Real-world problem:** You can't fix what you can't see — teams need to detect problems before customers do.
- **Business scenario:** The startup had an unnoticed outage last month. Leadership wants dashboards, alerts, and a documented incident response process.
- **Architecture:** Your app (from P1/P3) + Prometheus (scraping metrics) + Grafana (dashboards + alerts).
- **Technologies:** Docker/Kubernetes, Prometheus, Grafana.
- **Skills demonstrated:** Observability design, incident response, root-cause analysis, SRE-style documentation.
- **Infrastructure:** Reuses Project 3's cluster or Project 1's container host.
- **CI/CD:** Not the focus — reuse existing pipeline if applicable.
- **Security:** Grafana/Prometheus not exposed publicly without auth; scrape endpoints not leaking sensitive data.
- **Monitoring:** Full dashboard covering app health, resource usage, and at least 2 alert rules (e.g., high error rate, high latency).
- **Failure scenarios to simulate:** induced high CPU, induced high memory, forced application errors, pod/container killed mid-traffic, artificially slowed response time.
- **Troubleshooting scenarios:** alert fires but dashboard shows nothing (scrape misconfigured); alert never fires despite real problem (threshold/query wrong).
- **Expected repo structure:** `/monitoring` (prometheus config, dashboard export, alert rules), `README.md`, `docs/incident-reports/`.
- **README requirements:** architecture diagram, dashboard screenshots, alert rule explanations, links to incident reports.
- **Architecture diagram requirements:** show metrics flow: app → exporter → Prometheus → Grafana → alert.
- **Resume bullet points (examples):**
  - "Built a monitoring and alerting stack using Prometheus and Grafana, detecting and documenting 5 simulated production incidents."
  - "Authored incident reports and postmortems following simulated outages, including root-cause analysis and remediation steps."
- **Interview questions:** "Walk me through what your dashboard shows and why you chose those metrics." "An alert fires at 2am — what's your first move?" "What's the difference between monitoring, logging, and tracing, and where does this project sit?"
- **Possible improvements:** add log aggregation; add SLO-based alerting (burn rate); add automated remediation (e.g., auto-restart on failure) as a "self-healing" stretch goal.

---

## 11. TROUBLESHOOTING TRAINING — 30 SCENARIOS

### LINUX (5)

**1. "Permission denied" running a script**
- Symptoms: Script won't execute despite existing.
- Investigate: File permissions, execute bit, shebang line.
- Commands/tools: `ls -l`, `chmod`, `file`.
- Expected observation: Missing execute permission or wrong interpreter path.
- Root cause: Execute bit not set, or wrong shebang.
- Fix concept: Add execute permission; correct the shebang.
- Prevention: Set correct permissions at creation; use `chmod +x` in setup scripts.

**2. Disk full, service crashing**
- Symptoms: App fails to write files, logs show "No space left on device."
- Investigate: Disk usage by directory, largest files/logs.
- Commands/tools: `df -h`, `du -sh`, log rotation config.
- Expected observation: A log or temp directory has grown unbounded.
- Root cause: No log rotation configured.
- Fix concept: Clear/rotate logs, configure `logrotate`.
- Prevention: Set up log rotation and disk usage alerts proactively.

**3. Service won't start after reboot**
- Symptoms: App was running, but not after server restart.
- Investigate: Whether the service is enabled to start on boot.
- Commands/tools: `systemctl status`, `systemctl is-enabled`, `journalctl -b`.
- Expected observation: Service is not enabled at boot.
- Root cause: Missing `systemctl enable`.
- Fix concept: Enable the service for boot persistence.
- Prevention: Always enable + start when deploying a new service.

**4. High load average, sluggish server**
- Symptoms: Server responds slowly; users complain.
- Investigate: CPU/memory-hungry processes, zombie processes.
- Commands/tools: `top`/`htop`, `ps aux --sort=-%cpu`, `uptime`.
- Expected observation: A single runaway or looping process consuming CPU.
- Root cause: Application bug causing infinite loop or memory leak.
- Fix concept: Kill/restart offending process, then investigate application code/config.
- Prevention: Resource limits, monitoring, alerting on load thresholds.

**5. Cannot SSH into a server that was working yesterday**
- Symptoms: Connection times out or refused.
- Investigate: Network reachability, SSH service status, firewall changes.
- Commands/tools: `ping`, `telnet host 22` (or `nc`), `systemctl status sshd`, security group/firewall rules.
- Expected observation: Either SSH service down or firewall rule changed.
- Root cause: SSH daemon crashed, or a security rule was modified.
- Fix concept: Restart SSH service via console access, or correct the firewall/security group rule.
- Prevention: Change management process for firewall rules; monitoring for critical service uptime.

### NETWORKING (5)

**6. "Site can't be reached" for a newly deployed app**
- Symptoms: Browser can't resolve/connect to domain.
- Investigate: DNS resolution, whether DNS has propagated, correct record type.
- Commands/tools: `dig`/`nslookup`, `ping`.
- Expected observation: DNS record missing or pointing to wrong IP.
- Root cause: Incorrect or not-yet-propagated DNS record.
- Fix concept: Correct the record, wait for propagation (check TTL).
- Prevention: Verify DNS changes before announcing a launch; use lower TTL during migrations.

**7. App reachable internally, not externally**
- Symptoms: `curl localhost` works, external users get timeout.
- Investigate: Firewall/security group rules for the relevant port, whether the app binds to `0.0.0.0` vs `127.0.0.1`.
- Commands/tools: `netstat`/`ss -tulpn`, security group rules.
- Expected observation: App bound only to localhost, or port not open externally.
- Root cause: Misconfigured bind address or missing inbound rule.
- Fix concept: Bind app to `0.0.0.0` where appropriate; open the correct port in the security group.
- Prevention: Standardize bind configuration in deployment templates.

**8. Intermittent connection drops between two services**
- Symptoms: Requests fail randomly, not consistently.
- Investigate: Packet loss, connection pool exhaustion, timeouts.
- Commands/tools: `ping`/`mtr`, application connection pool settings, load balancer health check logs.
- Expected observation: Load balancer marking a healthy instance unhealthy intermittently.
- Root cause: Health check misconfiguration or resource exhaustion under load.
- Fix concept: Tune health check thresholds; scale resources or fix connection pooling.
- Prevention: Load testing before production; realistic health check tuning.

**9. HTTPS site shows certificate warning**
- Symptoms: Browser warns "connection not private."
- Investigate: Certificate expiry, correct domain match, chain of trust.
- Commands/tools: `openssl s_client`, browser certificate viewer.
- Expected observation: Expired certificate or mismatched domain.
- Root cause: Certificate not renewed or wrong cert installed.
- Fix concept: Renew/reissue certificate, ensure auto-renewal is configured.
- Prevention: Automate certificate renewal, monitor expiry dates.

**10. Two services on the same host can't communicate on expected port**
- Symptoms: Connection refused between local services.
- Investigate: Is the service actually listening on that port; firewall rules on the host itself.
- Commands/tools: `ss -tulpn`, local firewall (`iptables`/`ufw`) rules.
- Expected observation: Service listening on a different port than expected, or host firewall blocking it.
- Root cause: Configuration mismatch or overly restrictive local firewall.
- Fix concept: Correct the port config or firewall rule.
- Prevention: Document expected ports; consistent firewall configuration templates.

### DOCKER (5)

**11. Container exits immediately after starting**
- Symptoms: `docker ps` shows container not running right after `docker run`.
- Investigate: Container logs, entrypoint/CMD correctness.
- Commands/tools: `docker logs <container>`, `docker inspect`.
- Expected observation: Application crashes on startup due to missing config/dependency.
- Root cause: Missing environment variable or misconfigured entrypoint.
- Fix concept: Correct environment variables/command, verify app starts standalone first.
- Prevention: Test images locally with real config before deploying.

**12. "Image not found" / `ImagePullBackOff` style error**
- Symptoms: Docker/K8s can't pull the specified image.
- Investigate: Image name/tag correctness, registry authentication.
- Commands/tools: `docker pull` manually, registry login check.
- Expected observation: Typo in image tag, or missing registry credentials.
- Root cause: Wrong tag or unauthenticated registry access.
- Fix concept: Correct the tag, ensure proper registry login/credentials.
- Prevention: Use CI to build/tag images consistently; avoid manual tagging.

**13. Container can't connect to another container**
- Symptoms: Connection refused between app and database containers.
- Investigate: Whether both are on the same Docker network, correct service/hostname used.
- Commands/tools: `docker network inspect`, `docker exec` + ping/curl from inside container.
- Expected observation: Containers on different networks, or wrong hostname used.
- Root cause: Missing shared network or incorrect service name reference.
- Fix concept: Put both containers on the same custom network, reference by service name.
- Prevention: Use Docker Compose networks consistently rather than default bridge.

**14. Data disappears after container restart**
- Symptoms: Database resets every time the container restarts.
- Investigate: Whether a volume is mounted for the data directory.
- Commands/tools: `docker inspect` (Mounts section), Compose file review.
- Expected observation: No volume defined; data written to ephemeral container layer.
- Root cause: Missing volume mount for persistent data.
- Fix concept: Add a named volume or bind mount to the correct data path.
- Prevention: Always define volumes for stateful services from the start.

**15. Container works locally but fails in CI/production**
- Symptoms: `docker run` works on your machine, breaks elsewhere.
- Investigate: Environment differences (architecture, env vars, base image version).
- Commands/tools: `docker inspect`, compare `.env` files, check image digest vs tag.
- Expected observation: Different environment variables or a "latest" tag pointing to a different image than expected.
- Root cause: Environment drift or unpinned image versions.
- Fix concept: Pin exact image versions/digests; standardize env var management across environments.
- Prevention: Avoid `latest` tags in production; use `.env.example` and strict config validation.

### CI/CD (5)

**16. Pipeline fails only in CI, passes locally**
- Symptoms: Tests green locally, red in GitHub Actions.
- Investigate: Environment/dependency version differences, missing env vars in CI.
- Commands/tools: CI logs, compare local vs CI dependency versions.
- Expected observation: CI missing an environment variable or using a different dependency version.
- Root cause: Environment parity gap between local and CI.
- Fix concept: Align dependency versions (lockfiles), set required secrets/env vars in CI.
- Prevention: Use the same container/environment definitions for local dev and CI.

**17. Deployment succeeds but new code isn't live**
- Symptoms: Pipeline shows green, but users see old version.
- Investigate: Image tag/caching, whether the deployment step actually restarted the service.
- Commands/tools: Check running container's image digest, deployment step logs.
- Expected observation: Old image still cached/running; deploy step didn't force a restart.
- Root cause: Image tag reused (e.g., `latest`) without cache-busting, or deployment step misconfigured.
- Fix concept: Use unique tags per build (e.g., commit SHA); ensure deploy step forces pull/restart.
- Prevention: Tag images with commit SHA or build number, never rely solely on `latest`.

**18. Pipeline leaks a secret in logs**
- Symptoms: A secret value appears in plaintext in build logs.
- Investigate: Which step echoed the variable, whether masking is enabled.
- Commands/tools: Review workflow YAML step by step, CI secret masking settings.
- Expected observation: A debug/echo command printed the secret directly.
- Root cause: Improper handling of secret variables in scripts (e.g., `echo $SECRET`).
- Fix concept: Remove debug echoes of secrets; rely on the CI platform's built-in secret masking.
- Prevention: Code review pipeline changes; never print secret variables, even "temporarily for debugging."

**19. Pipeline randomly fails on flaky tests**
- Symptoms: Same commit sometimes passes, sometimes fails.
- Investigate: Test isolation, shared state between tests, timing/race conditions.
- Commands/tools: Re-run pipeline, review test logs for order-dependence.
- Expected observation: Tests depend on execution order or shared external state.
- Root cause: Non-deterministic or poorly isolated tests.
- Fix concept: Fix test isolation, add retries only as a stopgap, not a permanent fix.
- Prevention: Design tests to be independent and repeatable from the start.

**20. Deployment approval step never triggers**
- Symptoms: Pipeline stalls before production deploy indefinitely.
- Investigate: Environment protection rules, required reviewers configuration.
- Commands/tools: Review environment settings in GitHub repo, workflow run details.
- Expected observation: Approval rule misconfigured or reviewer not notified.
- Root cause: Incorrect environment protection setup.
- Fix concept: Correct the required-reviewers configuration for that environment.
- Prevention: Document and test approval gates when first setting them up, not after they're needed urgently.

### AWS (5)

**21. EC2 instance unreachable via SSH**
- Symptoms: Connection times out.
- Investigate: Security group inbound rules, instance state, correct key pair.
- Commands/tools: AWS console/CLI instance status checks, security group review.
- Expected observation: Security group missing inbound rule for port 22 from your IP.
- Root cause: Misconfigured or overly restrictive security group.
- Fix concept: Add correct inbound rule scoped to your IP.
- Prevention: Document required security group rules per service in IaC.

**22. S3 bucket access denied unexpectedly**
- Symptoms: Application or user gets "Access Denied" reading/writing S3.
- Investigate: Bucket policy, IAM policy attached to the role/user, public access block settings.
- Commands/tools: AWS console policy simulator, `aws s3 ls` with the relevant credentials.
- Expected observation: IAM policy doesn't grant the required action, or bucket policy conflicts.
- Root cause: Overly restrictive or missing IAM permission.
- Fix concept: Add the specific required permission (least privilege — not `s3:*`).
- Prevention: Test IAM policies in a sandbox before applying to production resources.

**23. Application can't reach the internet from a private subnet**
- Symptoms: Outbound requests (e.g., package updates) time out.
- Investigate: Route table for the private subnet, NAT gateway existence/configuration.
- Commands/tools: Review route tables in VPC console, `curl` test from the instance.
- Expected observation: No NAT gateway route configured for the private subnet.
- Root cause: Missing or misconfigured NAT gateway route.
- Fix concept: Add a route to a NAT gateway in the private subnet's route table.
- Prevention: Standardize VPC module design to always include NAT setup for private subnets that need outbound access.

**24. Unexpected AWS bill spike**
- Symptoms: Monthly cost far higher than expected.
- Investigate: Cost Explorer breakdown by service, orphaned/unused resources.
- Commands/tools: AWS Cost Explorer, `aws ec2 describe-instances` for forgotten running instances.
- Expected observation: Forgotten running EC2 instances or unattached EBS volumes/NAT gateways left on.
- Root cause: Resources not cleaned up after testing.
- Fix concept: Terminate unused resources; set up budget alerts.
- Prevention: Always `terraform destroy` learning environments when done; set AWS Budget alerts from day one.

**25. CloudWatch alarm never triggers despite real problem**
- Symptoms: Server is clearly overloaded, but no alert fired.
- Investigate: Alarm threshold, evaluation period, whether the metric is actually being published.
- Commands/tools: CloudWatch console metric graph, alarm configuration review.
- Expected observation: Threshold set too high, or wrong metric/dimension selected.
- Root cause: Misconfigured alarm.
- Fix concept: Correct the threshold/metric and evaluation period based on real data.
- Prevention: Test alarms by intentionally triggering the condition once during setup.

### KUBERNETES (5)

**26. Pod stuck in `Pending`**
- Symptoms: Pod never reaches `Running`.
- Investigate: Resource requests vs available node capacity, scheduling constraints.
- Commands/tools: `kubectl describe pod`, `kubectl get nodes -o wide`, `kubectl top nodes`.
- Expected observation: Events show "Insufficient CPU/memory" or unmatched node selector.
- Root cause: Resource requests too high for available nodes, or scheduling constraint unmet.
- Fix concept: Lower resource requests, add nodes, or fix node selector/affinity rules.
- Prevention: Right-size resource requests based on actual usage; monitor cluster capacity.

**27. `CrashLoopBackOff`**
- Symptoms: Pod repeatedly restarts.
- Investigate: Container logs from previous crash, exit code, liveness probe config.
- Commands/tools: `kubectl logs <pod> --previous`, `kubectl describe pod`.
- Expected observation: Application crashing on startup, or an overly aggressive liveness probe killing a slow-starting app.
- Root cause: App-level bug/misconfiguration or probe misconfigured relative to actual startup time.
- Fix concept: Fix the underlying app issue, or adjust probe `initialDelaySeconds`/thresholds.
- Prevention: Test startup time under realistic conditions before setting probe values.

**28. `ImagePullBackOff`**
- Symptoms: Pod can't pull its container image.
- Investigate: Image name/tag correctness, registry credentials (imagePullSecrets).
- Commands/tools: `kubectl describe pod`, manual `docker pull` of the same image/tag.
- Expected observation: Typo in image reference or missing/incorrect `imagePullSecrets`.
- Root cause: Incorrect image reference or missing registry auth in the cluster.
- Fix concept: Correct the image tag; configure the correct pull secret.
- Prevention: Validate manifests against the actual registry before applying; use CI to generate correct image references automatically.

**29. Service returns connection refused despite healthy pods**
- Symptoms: `kubectl get pods` shows Running, but Service doesn't route traffic correctly.
- Investigate: Service selector labels vs pod labels, targetPort vs containerPort match.
- Commands/tools: `kubectl describe service`, `kubectl get pods --show-labels`.
- Expected observation: Selector doesn't match any pod labels, or wrong target port.
- Root cause: Label/selector mismatch or port misconfiguration.
- Fix concept: Align Service selector with pod labels; correct targetPort to match the container's actual listening port.
- Prevention: Keep labels consistent and intentional across manifests; review before applying.

**30. Rolling update causes downtime instead of zero-downtime**
- Symptoms: Users experience errors during a deployment update.
- Investigate: Readiness probe presence/configuration, rolling update strategy settings (maxUnavailable/maxSurge).
- Commands/tools: `kubectl rollout status`, `kubectl describe deployment`.
- Expected observation: No readiness probe (traffic sent to not-yet-ready pods), or `maxUnavailable` too aggressive.
- Root cause: Missing readiness probe or misconfigured rollout strategy.
- Fix concept: Add a proper readiness probe; tune `maxUnavailable`/`maxSurge` for safer rollout.
- Prevention: Always define readiness probes before considering a deployment "production-like."

---

## 12. INTERVIEW QUESTION BANK

*(Practice these by answering out loud or in writing first, then checking your answer against documentation or asking AI to critique — never memorize AI-generated answers verbatim.)*

### Linux (30)
1. What is the Linux filesystem hierarchy and what lives in `/etc`, `/var`, `/home`, `/usr`?
2. Explain file permissions and what `chmod 755` means.
3. Difference between hard link and symbolic link?
4. How do you find which process is using a specific port?
5. What does `kill -9` actually do, and why is it a last resort?
6. Explain the difference between a process and a thread.
7. What is a zombie process?
8. How does `systemctl` differ from the older `service` command?
9. What's stored in `/var/log`, and how would you investigate a crash?
10. Explain environment variables and how to persist them.
11. What's the difference between `su` and `sudo`?
12. How do you check disk usage and find what's consuming space?
13. What is a symbolic vs. absolute path?
14. Explain how cron jobs work.
15. What does `chown` do, and when would you use it vs `chmod`?
16. Difference between `>` and `>>` in Bash redirection?
17. How would you check memory usage on a Linux box?
18. What is a package manager, and how does apt differ from yum?
19. Explain the boot process at a high level.
20. What is an inode?
21. How do you find and terminate a runaway process consuming CPU?
22. What's the difference between a soft limit and a hard limit for resources?
23. Explain SSH key-based authentication vs password authentication.
24. What does `ssh-keygen` generate, and what's the difference between the public and private key?
25. How would you troubleshoot "connection refused" on a server?
26. What is `nohup` used for?
27. Explain file descriptors at a conceptual level.
28. How do you check which services are set to start on boot?
29. What's the purpose of `/etc/fstab`?
30. How would you rotate logs to prevent disk space issues?

### Networking (25)
1. Explain the OSI model layers in your own words.
2. What's the difference between TCP and UDP?
3. Explain the TCP three-way handshake.
4. What is DNS, and what's the difference between an A record and a CNAME?
5. What happens when you type a URL into your browser and press Enter?
6. What is a subnet, and why do we use them?
7. Difference between a public and private IP address?
8. What is NAT, and why is it needed?
9. Explain the difference between a forward proxy and a reverse proxy.
10. What's a load balancer, and what problem does it solve?
11. Explain HTTP status code categories (2xx, 3xx, 4xx, 5xx).
12. What's the difference between HTTP and HTTPS?
13. Explain the TLS handshake at a conceptual level.
14. What is a firewall, and how does it differ from a security group?
15. What port does SSH use by default, and can you change it?
16. What is a VPN, conceptually?
17. Explain the difference between a stateful and stateless firewall.
18. What's an Internet Gateway vs a NAT Gateway (AWS context)?
19. How does DHCP work?
20. What's the difference between latency and bandwidth?
21. Explain what a CDN does and why it improves performance.
22. What is packet loss, and how would you diagnose it?
23. What's a MAC address vs an IP address?
24. Explain the difference between Layer 4 and Layer 7 load balancing.
25. How would you troubleshoot "site not resolving" for a domain?

### Git (20)
1. What's the difference between `git merge` and `git rebase`?
2. How do you resolve a merge conflict?
3. What is a detached HEAD state?
4. Explain `git fetch` vs `git pull`.
5. What's the purpose of a `.gitignore` file?
6. How do you undo the last commit without losing changes?
7. What's the difference between `git reset` and `git revert`?
8. Explain branching strategy (e.g., feature branches, trunk-based).
9. What is a pull request, and why use one instead of pushing directly to main?
10. How do you squash commits before merging?
11. What's a git tag used for?
12. Explain `git stash` and when you'd use it.
13. What happens during a fast-forward merge?
14. How would you find which commit introduced a bug?
15. What is `git cherry-pick`?
16. Explain the three areas in Git: working directory, staging area, repository.
17. How do you remove a file from Git history entirely (conceptually)?
18. What's the difference between a fork and a clone?
19. How do you handle a large binary file in Git (conceptually — LFS)?
20. What's your process when you accidentally commit a secret?

### Docker (25)
1. What's the difference between an image and a container?
2. Explain Docker image layering and why it matters for build speed.
3. What's the purpose of a `.dockerignore` file?
4. Difference between `CMD` and `ENTRYPOINT` (conceptually)?
5. What is a multi-stage build, and why use one?
6. Explain the difference between a named volume and a bind mount.
7. How does container networking work by default (bridge network)?
8. What's the difference between `docker run` and `docker exec`?
9. How would you debug a container that exits immediately?
10. What is Docker Compose, and what problem does it solve?
11. Explain the difference between `EXPOSE` and actually publishing a port.
12. What happens to data inside a container when it's removed?
13. How do you pass environment variables into a container securely?
14. What is a base image, and how do you choose one responsibly?
15. Explain image tagging best practices (`latest` vs pinned versions).
16. What's the purpose of a container registry?
17. How would you reduce the size of a Docker image?
18. What is the difference between `docker stop` and `docker kill`?
19. Explain how Docker health checks work.
20. What's a common cause of "port already in use" errors?
21. How do you inspect what's happening inside a running container?
22. What's the risk of running a container as root?
23. Explain the difference between build-time and run-time configuration.
24. How would you troubleshoot two containers that can't communicate?
25. What's the purpose of Docker's layer caching during builds?

### CI/CD (25)
1. What's the difference between Continuous Integration and Continuous Deployment?
2. Explain what a CI/CD pipeline stage is.
3. What is a "runner" in GitHub Actions?
4. How do you securely manage secrets in a pipeline?
5. What triggers a GitHub Actions workflow?
6. Explain the difference between an artifact and an image in a pipeline context.
7. What's a deployment strategy — name a few (rolling, blue/green, canary) conceptually.
8. How would you set up a manual approval gate before production deployment?
9. What's the purpose of environment-specific configuration in a pipeline?
10. How do you handle rollback if a deployment fails?
11. What's a common cause of a pipeline passing but the deployment not reflecting new code?
12. Explain caching in CI/CD pipelines and its benefits/risks.
13. How would you debug a pipeline that fails only in CI, not locally?
14. What's the difference between a build stage and a test stage?
15. How do you prevent a secret from leaking into pipeline logs?
16. What's a matrix build, conceptually?
17. Explain why you shouldn't deploy directly to production without any gate.
18. What's the purpose of tagging images with a commit SHA instead of `latest`?
19. How would you structure a pipeline for multiple environments (dev/staging/prod)?
20. What's the difference between Jenkins and GitHub Actions at a conceptual level?
21. How do pipeline notifications/alerts fit into a good CI/CD setup?
22. What's "shift-left" in the context of CI/CD and security?
23. How would you handle flaky tests in a pipeline?
24. What's the purpose of a staging environment before production?
25. Explain how you'd design a pipeline for zero-downtime deployment.

### AWS (40)
1. What is IAM, and what's the difference between a user and a role?
2. What is least privilege, and why does it matter?
3. Explain the difference between EC2 and a container service like ECS.
4. What is a security group, and how does it differ from a NACL?
5. What's the difference between a public and private subnet?
6. Explain what a VPC is and why it exists.
7. What is an Internet Gateway?
8. What is a NAT Gateway, and when would you need one?
9. Explain S3 — what is it used for, and how is it structured (buckets/objects)?
10. What is an S3 bucket policy vs an IAM policy — how do they interact?
11. What is ECR, and how does it relate to Docker Hub?
12. Explain CloudWatch — logs vs metrics vs alarms.
13. What is an Availability Zone vs a Region?
14. What's the difference between an Elastic IP and a regular public IP?
15. Explain the shared responsibility model in AWS.
16. What's an AMI?
17. How would you securely give an application running on EC2 access to S3 (conceptually)?
18. What's the difference between a Network Load Balancer and an Application Load Balancer?
19. What is Route 53 used for?
20. Explain what an EBS volume is vs instance store.
21. What's the purpose of tagging AWS resources?
22. How would you estimate/control AWS costs on a project?
23. What is an Auto Scaling Group, conceptually?
24. Explain the difference between IAM policies and resource-based policies.
25. What's a VPC peering connection?
26. What is AWS CloudTrail used for?
27. Explain what happens if you make an S3 bucket public accidentally — risks and fixes.
28. What's the difference between a stopped and terminated EC2 instance?
29. What is an IAM policy document structured around (Effect, Action, Resource)?
30. How would you rotate AWS access keys safely?
31. What's the purpose of a bastion host?
32. Explain how you'd design a highly available architecture across AZs, conceptually.
33. What's the difference between RDS and running your own database on EC2?
34. What is an AWS Lambda function, conceptually, and when might you use one vs EC2?
35. How does encryption at rest vs in transit apply to AWS services?
36. What's the purpose of AWS Organizations / multi-account strategy, conceptually?
37. How would you troubleshoot "access denied" on an S3 object?
38. What's a VPC endpoint, conceptually?
39. Explain how you'd secure secrets used by an application on AWS (e.g., Secrets Manager vs env vars).
40. What would you check first if your AWS bill suddenly spiked?

### Terraform (25)
1. What is Infrastructure as Code, and why does it matter?
2. What's the difference between declarative and imperative IaC?
3. What is Terraform state, and why is it important?
4. What problems occur with local state in a team environment?
5. What is a Terraform provider?
6. Explain the difference between a resource and a data source.
7. What's the purpose of Terraform variables and outputs?
8. What is a Terraform module, and why use one?
9. Explain `terraform plan` vs `terraform apply`.
10. What happens during `terraform destroy`?
11. What is state drift, and how would you detect it?
12. Explain remote state and why it's preferred for teams.
13. What is state locking, and what problem does it solve?
14. How would you structure Terraform code for multiple environments (dev/staging/prod)?
15. What's the risk of committing a `.tfstate` file to a public Git repo?
16. Explain Terraform's dependency graph — how does it know resource creation order?
17. What is a Terraform workspace, conceptually?
18. How would you import an existing manually-created resource into Terraform?
19. What's the difference between `count` and `for_each` in Terraform, conceptually?
20. How do you handle secrets (e.g., DB passwords) in Terraform responsibly?
21. What happens if two team members run `terraform apply` simultaneously without locking?
22. Explain the purpose of `terraform fmt` and `terraform validate`.
23. What's a provisioner in Terraform, and why is it generally discouraged for primary logic?
24. How would you safely refactor a large Terraform config into modules without destroying existing resources?
25. What's your process for reviewing a `terraform plan` output before applying to production?

### Kubernetes (40)
1. Explain Kubernetes architecture — control plane vs worker nodes.
2. What is a pod, and why doesn't Kubernetes just manage containers directly?
3. What's the difference between a Deployment and a ReplicaSet?
4. Explain what a Service does and the difference between ClusterIP, NodePort, and LoadBalancer.
5. What is a namespace, and why use one?
6. Explain ConfigMaps vs Secrets — when would you use each?
7. What is an Ingress, and how does it differ from a Service?
8. Explain liveness probes vs readiness probes.
9. What is a rolling update, and how does Kubernetes perform one?
10. How would you roll back a bad deployment?
11. What is a PersistentVolume vs a PersistentVolumeClaim?
12. Explain what `CrashLoopBackOff` means and how you'd diagnose it.
13. What causes `ImagePullBackOff`, and how do you fix it?
14. Why might a pod stay stuck in `Pending`?
15. Explain how Kubernetes scheduling decides which node runs a pod.
16. What is a HorizontalPodAutoscaler, conceptually?
17. What's the difference between a StatefulSet and a Deployment?
18. What is a DaemonSet used for?
19. Explain resource requests vs limits for a container.
20. What is `kubectl describe` useful for that `kubectl get` isn't?
21. How would you view logs for a crashed pod that already restarted?
22. What is a label vs a selector in Kubernetes?
23. Explain the purpose of a Kubernetes Secret and how it differs from just an env var in a Deployment.
24. What happens when you delete a pod managed by a Deployment?
25. Explain the concept of desired state vs actual state (reconciliation loop).
26. What's the difference between `maxUnavailable` and `maxSurge` in a rolling update?
27. What is a Kubernetes Job vs a CronJob?
28. How would you debug a Service that isn't routing traffic to any pods?
29. What is node affinity, conceptually?
30. What's the difference between a taint and a toleration?
31. How would you safely drain a node for maintenance?
32. What's the purpose of an admission controller, conceptually?
33. Explain how DNS resolution works inside a Kubernetes cluster (service discovery).
34. What is etcd's role in a Kubernetes cluster?
35. How would you troubleshoot a networking issue between two pods in different namespaces?
36. What's the difference between a Kubernetes Operator and a standard Deployment, conceptually?
37. What is a sidecar container pattern?
38. How does Kubernetes handle secrets at rest by default, and why might that matter for security?
39. What's your process for diagnosing "deployment applied but nothing changed"?
40. How would you explain Kubernetes' value to someone who only knows Docker Compose?

### Monitoring (20)
1. What's the difference between monitoring, logging, tracing, and observability?
2. What is a metric, and how does Prometheus collect them?
3. Explain what an exporter is in the Prometheus ecosystem.
4. What is PromQL, and what's it used for?
5. What's the difference between a counter, gauge, histogram (conceptually)?
6. What is a Grafana dashboard, and how does it relate to Prometheus?
7. How would you design an alert that avoids being too noisy?
8. What's the difference between a symptom-based alert and a cause-based alert?
9. Explain what an SLI and SLO are, conceptually.
10. What's alert fatigue, and how do you avoid causing it?
11. How would you investigate a spike in error rate shown on a dashboard?
12. What's the value of correlating logs with metrics during an incident?
13. What is a scrape interval, and why does it matter?
14. How would you set up an alert for "service is down"?
15. What's the difference between proactive and reactive monitoring?
16. Why is dashboard design (not just data collection) important?
17. What's a runbook, and why attach one to an alert?
18. How would you monitor a system you didn't build yourself?
19. What's the risk of only monitoring infrastructure metrics and not application-level metrics?
20. How would you explain to a non-technical stakeholder why monitoring matters?

### DevSecOps (20)
1. What does "shift-left security" mean?
2. Why shouldn't secrets be hardcoded in code or config files?
3. What is image scanning, and why run it in a pipeline?
4. What's the difference between authentication and authorization?
5. What is least privilege, and how does it apply to CI/CD pipelines specifically?
6. What's a dependency vulnerability scan, and why does it matter?
7. How would you securely manage secrets across multiple environments?
8. What's the risk of an overly permissive security group in production?
9. Explain the principle of defense in depth.
10. What's the purpose of network segmentation?
11. How would you handle a leaked secret discovered in Git history?
12. What is a security baseline for a container image?
13. Why is running containers as non-root recommended?
14. What's the purpose of a Web Application Firewall, conceptually?
15. How would you approach securing Kubernetes Secrets beyond default base64 encoding?
16. What's the value of automated compliance checks in a pipeline?
17. Explain the concept of "blast radius" and why it matters in incident planning.
18. How would you audit who has access to what in a cloud account?
19. What's a common security mistake teams make when moving fast in CI/CD?
20. How would you balance developer velocity with security requirements?

### Scenario-Based "What Would You Do If…" (30)
1. Production is down and you don't know why — what's your first 5 minutes?
2. A deployment just went out and error rates spiked immediately — what do you do?
3. You accidentally pushed a secret to a public GitHub repo — what's your process?
4. A teammate asks you to bypass a security group rule "just for now" — how do you respond?
5. Your Terraform apply partially failed midway — what's your next step?
6. A pod is in CrashLoopBackOff at 2am and you're on call — walk through your process.
7. Your CI/CD pipeline is green but the client says the site is still broken — what do you check?
8. You notice unexpected AWS charges — what's your investigation process?
9. A colleague wants to skip code review to "ship fast" — how do you handle it?
10. You inherit an undocumented production system — how do you start understanding it?
11. Your monitoring shows high memory usage trending upward over days — what do you suspect and check?
12. A rollback needs to happen immediately during an incident — walk through it.
13. You're asked to give a third-party vendor AWS access — how do you scope it safely?
14. Your Kubernetes cluster suddenly can't schedule any new pods — what do you check?
15. A database migration in a pipeline fails halfway — what's your recovery approach?
16. You're asked to reduce cloud costs by 30% — where do you start looking?
17. Two engineers' Terraform changes conflict and cause drift — how do you resolve it?
18. Your load balancer health checks are failing intermittently — how do you investigate?
19. A critical alert fires but you can't reproduce the issue — what do you do?
20. You're asked to onboard a new engineer quickly to your infra — what documentation/access do you prepare?
21. Your Docker image size ballooned overnight in CI — how do you find out why?
22. A security scan flags a vulnerability in a base image you use everywhere — how do you triage?
23. Your DNS provider has an outage — what's your immediate mitigation, if any?
24. You need to migrate a stateful application to Kubernetes — what are your biggest concerns?
25. Your team wants to adopt a new tool you've never used — how do you evaluate it?
26. A postmortem reveals the root cause was "we didn't have monitoring on that service" — what do you propose?
27. You're debugging an issue and AI suggests a fix involving `chmod 777` — how do you respond?
28. Your staging environment doesn't match production and a bug slipped through — how do you prevent recurrence?
29. You need to explain a technical incident to a non-technical manager — how do you structure it?
30. You're given a vague ticket: "the app is slow sometimes" — how do you approach investigating it?

---

## 13. FULL MOCK INTERVIEW SIMULATION

Run this as a self-timed simulation (or with a study partner / AI as interviewer, answering yourself first).

**Round 1 — Linux + Networking (20 min):** Pull 8 questions from those banks at random. Include at least one troubleshooting scenario read aloud (Scenario 5 or 6) and diagnose it live.

**Round 2 — Docker + Git + CI/CD (20 min):** Pull 8 questions. Include Scenario 15 (Docker) and Scenario 17 (CI/CD) as live diagnosis exercises.

**Round 3 — AWS + Terraform (20 min):** Pull 8 questions. Include Scenario 23 (AWS) as a live diagnosis exercise.

**Round 4 — Kubernetes + Monitoring (20 min):** Pull 8 questions. Include Scenario 27 (Kubernetes) as a live diagnosis exercise.

**Round 5 — Project Deep Dive (20 min):** Interviewer picks ONE of your 4 projects and asks hard, specific questions designed to catch memorization rather than understanding, such as:
- "Why did you choose this architecture over [alternative]?"
- "What would break first if this had 10x the traffic?"
- "If I removed this specific component, what would fail, and why?"
- "What's the worst decision you made in this project, and what would you do differently?"
- "Show me the exact commit/line where you handled [specific security concern]."

**Round 6 — Troubleshooting (15 min):** Interviewer reads out a scenario (from the 30 above, unseen order) with only symptoms — no root cause given — and you must talk through diagnosis live, asking clarifying questions as needed.

**Round 7 — Behavioral (15 min):** Standard behavioral questions adapted for a fresher: "Tell me about a time you were stuck on a technical problem — how did you get unstuck?" "Tell me about a mistake you made in one of your projects and what you learned." "How do you approach learning something you don't know?" "Why DevOps, and why should we hire someone without professional experience?"

**After each round:** score yourself honestly (1–5) on clarity, correctness, and confidence, then note specific gaps to revisit.

---

## 14. JOB APPLICATION STRATEGY

### Primary roles to apply for
DevOps Engineer Trainee · Junior DevOps Engineer · Cloud/DevOps Engineer · Cloud Support Engineer · Junior Cloud Engineer

### Secondary roles (apply, but expect more competition or a longer shot)
Build & Release Engineer · Junior Infrastructure Engineer · Junior SRE · Platform Engineer Trainee · DevSecOps Trainee

**Why secondary:** SRE, Platform Engineering, and DevSecOps roles — even "junior" titled — often expect either prior ops/dev experience or deeper specialization than a 3-month roadmap builds. Apply anyway if a posting looks genuinely entry-level, but don't center your search there.

### Job descriptions to avoid (red flags for a fresher)
- "3–5 years experience" listed as a requirement for a role titled "Junior" or "Trainee" (contradictory posting — often a mismatch or unrealistic expectation)
- Requires expert-level in 3+ clouds simultaneously
- Requires specific enterprise tools with no room to learn (e.g., "must already be certified in X obscure vendor tool")
- No mention of mentorship/onboarding for a role calling itself "entry-level"
- Compensation far below local market rate for the listed responsibilities (may indicate exploitative expectations)

---

## 15. JOB DESCRIPTION ANALYSIS FRAMEWORK

When reading any JD, sort every requirement into:

| Bucket | Meaning | Example |
|---|---|---|
| **Must-have** | You need this on day one or you can't do the job at all | Basic Linux, Git |
| **Important** | Strongly expected, gaps are noticeable but coachable | Docker, basic CI/CD |
| **Nice-to-have** | Bonus, differentiates you from other freshers | Kubernetes exposure, Terraform |
| **Can learn after joining** | Company expects on-the-job ramp-up | Their specific internal tools, a specific cloud you haven't used |
| **Red flag** | Signals unrealistic expectations or poor role definition | "Expert in 5 clouds," "must have 3 yrs experience" for trainee role |

**Comparison method:** List every requirement from the JD in one column, then honestly mark your level (Not started / Learning / Practicing / Can build / Can troubleshoot / Interview ready) next to each. If 70%+ of "must-have" and "important" items are at "Practicing" or above, apply.

---

## 16. RESUME STRATEGY

**Structure:**
- **Headline:** e.g., "Aspiring DevOps Engineer | Docker · CI/CD · AWS · Terraform · Kubernetes" — not "DevOps Expert."
- **Technical skills:** grouped by category (Languages/Scripting, Containers, Cloud, IaC, CI/CD, Monitoring) — list only what you can actually discuss under pressure.
- **Projects:** your strongest section as a fresher. 3–4 bullet points per project, action-oriented, honest.
- **GitHub:** link prominently near the top.
- **Certifications:** list if earned; don't pad with "in progress" unless truly close.
- **Education:** standard, brief.
- **Achievements:** only real, verifiable ones.

**Do NOT fabricate experience.** Describe projects as projects — "Designed and deployed a personal project that…" not "Led a team that…" if it wasn't true. Interviewers probe project depth specifically because resume padding is common; honesty plus depth of understanding beats an inflated resume every time.

**Example strong bullet structures (adapt with your own specifics, don't copy verbatim):**
- "[Action verb] a [what] using [tools] that [result/capability], demonstrating [skill]."
- "Diagnosed and resolved [number] simulated production failures across [systems], documenting root cause and remediation for each."
- "Reduced [some measurable thing you actually measured] by [real number] through [specific action]." — only include numbers you can defend if asked exactly how you measured them.

---

## 17. GITHUB PORTFOLIO STRATEGY

Every major project repo should contain:
- Clear `README.md` (problem, architecture, setup, and usage — a stranger should be able to run it)
- Architecture diagram (image or Mermaid-style text diagram)
- Prerequisites section
- Setup/deployment explanation
- CI/CD explanation (if applicable)
- Security explanation (what you secured and why)
- Monitoring explanation (if applicable)
- Dedicated troubleshooting/failure-scenarios section
- Screenshots where visual (dashboards, pipeline runs)
- "Lessons learned" section (genuine reflection, including what you'd do differently)
- "Future improvements" section

**Profile-level polish:** pinned repos = your 4 projects, a clean profile README summarizing your focus areas, consistent commit history (not one giant commit dump the night before applying), and no half-finished abandoned repos left visible without at least a "status: paused, here's why" note.

---

## 18. LEARNING TRACKER — 12-WEEK CHECKLIST

Status options: `Not Started` → `Learning` → `Practicing` → `Can Build` → `Can Troubleshoot` → `Interview Ready`

**Linux:**
- [ ] Fundamentals & filesystem
- [ ] Permissions & ownership
- [ ] Processes & services
- [ ] Package management
- [ ] Logs & journalctl
- [ ] SSH (key-based)
- [ ] Troubleshooting
- [ ] Interview ready

**Networking:**
- [ ] OSI/TCP-IP model
- [ ] DNS
- [ ] Ports & protocols
- [ ] HTTP/HTTPS/TLS
- [ ] Firewalls/security groups
- [ ] Load balancer concept
- [ ] Troubleshooting
- [ ] Interview ready

**Git:**
- [ ] Basics (commit/branch/merge)
- [ ] Conflict resolution
- [ ] Pull requests / workflows
- [ ] Troubleshooting
- [ ] Interview ready

**Bash:**
- [ ] Variables/conditionals/loops
- [ ] Functions & arguments
- [ ] Automation scripts
- [ ] Interview ready

**Docker:**
- [ ] Images vs containers
- [ ] Dockerfile writing
- [ ] Volumes & networking
- [ ] Docker Compose
- [ ] Troubleshooting
- [ ] Interview ready

**CI/CD:**
- [ ] CI/CD concepts
- [ ] GitHub Actions workflows
- [ ] Secrets management
- [ ] Build/test/deploy pipeline
- [ ] Troubleshooting
- [ ] Interview ready

**AWS:**
- [ ] IAM (users/roles/policies)
- [ ] EC2
- [ ] S3
- [ ] VPC/networking
- [ ] ECR
- [ ] CloudWatch
- [ ] Troubleshooting
- [ ] Interview ready

**Terraform:**
- [ ] Core concepts & resources
- [ ] Variables/outputs
- [ ] State management
- [ ] Modules
- [ ] Plan/apply/destroy workflow
- [ ] Troubleshooting
- [ ] Interview ready

**Kubernetes:**
- [ ] Architecture
- [ ] Pods/Deployments/Services
- [ ] ConfigMaps/Secrets
- [ ] Ingress
- [ ] Health checks & rolling updates
- [ ] Scaling concepts
- [ ] Troubleshooting
- [ ] Interview ready

**Monitoring (Prometheus/Grafana):**
- [ ] Metrics & scraping
- [ ] PromQL basics
- [ ] Dashboards
- [ ] Alert rules
- [ ] Interview ready

**Security:**
- [ ] Least privilege
- [ ] Secrets management
- [ ] Image scanning basics
- [ ] Network security basics
- [ ] Interview ready

**AI-Assisted DevOps:**
- [ ] Structured troubleshooting prompts
- [ ] Safe usage (never leaking secrets)
- [ ] Using AI for interview prep correctly

**Projects:**
- [ ] Project 1 — Automated Delivery Platform
- [ ] Project 2 — IaC Cloud Platform
- [ ] Project 3 — Kubernetes Platform
- [ ] Project 4 — Observability Platform

---

## 19. LEARNING RESOURCES

*(A small number of high-quality resources per topic — not 20 courses. Official docs are prioritized. Search for current versions/links since docs and free-tier offers change.)*

| Topic | Free | Paid (optional) | Official docs |
|---|---|---|---|
| Linux | freeCodeCamp Linux courses, Linux Journey (linuxjourney.com) | — | `man` pages, distro docs (Ubuntu/Debian docs) |
| Networking | Practical Networking (YouTube/blog) | — | N/A (concept-based, cross-reference multiple sources) |
| Git/GitHub | Git's own tutorial, GitHub Docs "Git Handbook" | — | git-scm.com/doc, docs.github.com |
| Docker | Docker's official "Get Started" guide | — | docs.docker.com |
| GitHub Actions | GitHub's own Actions quickstart | — | docs.github.com/actions |
| AWS | AWS Skill Builder free tier, AWS "Cloud Practitioner Essentials" | AWS Certified courses (if pursuing cert) | docs.aws.amazon.com |
| Terraform | HashiCorp's own Terraform tutorials (learn.hashicorp.com) | — | developer.hashicorp.com/terraform |
| Kubernetes | Kubernetes official tutorials, "Kubernetes the Hard Way" (for deep understanding, optional) | — | kubernetes.io/docs |
| Prometheus | Prometheus official docs' "Getting Started" | — | prometheus.io/docs |
| Grafana | Grafana official "Getting Started" | — | grafana.com/docs |

---

## 20. CERTIFICATIONS

**Are they necessary?** No — not for a first junior/trainee role. Strong projects and clear communication typically matter more than a badge for entry-level hiring. Certifications become more valuable as a *tiebreaker* or when a JD explicitly lists one as a hard requirement (common for some Cloud Support roles).

| Certification | Usefulness at fresher stage | When to attempt |
|---|---|---|
| AWS Certified Cloud Practitioner | Optional, good for Cloud Support-style roles | After Month 2, if targeting AWS-heavy roles |
| AWS Certified Solutions Architect – Associate | Useful but more mid-level focused | After the roadmap, months 4–6 |
| HashiCorp Terraform Associate | Nice signal, aligns well with Project 2 | After Week 10, if you want it |
| Kubernetes (CKA/CKAD) | Valuable but genuinely hard for a 3-month beginner | Months 6+ after real hands-on depth |

**Can projects substitute for certifications at beginner level?** Largely yes. A hiring manager reviewing a junior candidate usually finds a well-documented, well-explained project more convincing than a cert with no depth behind it — but a cert *plus* a real project is stronger than either alone.

---

## 21. WHAT NOT TO LEARN YET

| Skip for now | Why |
|---|---|
| Multiple clouds simultaneously (AWS + Azure + GCP) | Depth in one beats shallow breadth across three; employers value real proficiency over buzzword coverage |
| Multiple CI/CD tools (GitHub Actions + Jenkins + GitLab CI + CircleCI) | Core concepts transfer between tools; master one deeply first |
| Every Kubernetes feature (Operators, CRDs, service mesh, multi-cluster) | These are advanced/platform-team concerns; juniors are evaluated on fundamentals |
| Multiple configuration-management tools (Ansible + Chef + Puppet + Terraform) | Terraform alone covers your IaC needs for this stage |
| Advanced service meshes (Istio, Linkerd) | Requires solid Kubernetes fundamentals first; premature otherwise |
| Advanced distributed systems theory | Valuable eventually, not need-to-know for junior hiring |
| Full enterprise observability stacks (ELK + Loki + Tempo + Prometheus + Grafana + more) | Prometheus + Grafana alone teaches the core concepts; stacking tools now just slows you down |

**Principle:** depth in the fundamentals beats a scattershot tour of every trending tool. Employers can teach you their specific stack; they're hiring for how well you think and troubleshoot.

---

## 22. FINAL JOB-READINESS EXAM & SKILL MATRIX

### The exam
**Scenario:** A fictional startup, "NimbusCart," has an e-commerce web app currently running on a single developer's laptop with no automation, no monitoring, and manual "just SCP the files over" deployments. They've hired you as their first DevOps hire.

**Your task (in order):**
1. Analyze their stated requirements (assume: needs reliability, some traffic spikes expected, small team, cost-conscious) and write a short requirements analysis.
2. Design an architecture (diagram + written explanation) covering compute, networking, and deployment approach.
3. Provision the infrastructure using Terraform.
4. Containerize the application.
5. Build a CI/CD pipeline (test → build → deploy).
6. Deploy it (to EC2 or Kubernetes — your choice, justify it).
7. Set up monitoring (Prometheus/Grafana) with at least 2 meaningful alerts.
8. Apply security best practices (IAM least privilege, secrets management, no open security groups).
9. Simulate at least 3 failures and document your diagnosis and fix for each.
10. Write full documentation (README, architecture diagram, runbook, incident report template).

**No solution is provided here on purpose** — this exam is meant to combine everything from Weeks 1–12 into one project you design end-to-end. If you can complete this without needing to look up basic concepts (looking up specific syntax is fine), you are genuinely ready to start interviewing seriously.

### Evaluation rubric

| Area | Weak (1) | Adequate (2) | Strong (3) |
|---|---|---|---|
| Requirements analysis | Skipped or vague | Basic bullet list | Clear, ties decisions back to stated needs |
| Architecture design | No diagram, unclear reasoning | Diagram present, some gaps | Clear diagram, every choice justified |
| Infrastructure as Code | Manual console usage or broken Terraform | Terraform works but messy/monolithic | Modular, reusable, documented Terraform |
| Containerization | App doesn't run in container reliably | Works but unoptimized image | Clean, small, well-structured image |
| CI/CD | No automation or broken pipeline | Basic pipeline works | Full test→build→deploy with secrets handled properly |
| Deployment | Manual step required | Deploys automatically | Automated + resilient (health checks, rollback) |
| Monitoring | None or dashboard with no alerts | Basic dashboard | Dashboard + meaningful, tested alerts |
| Security | Open security groups, hardcoded secrets | Some gaps addressed | Least privilege throughout, no hardcoded secrets |
| Troubleshooting | Can't explain failures found | Explains what happened | Explains root cause + prevention clearly |
| Documentation | Minimal/missing | Covers basics | Complete, a stranger could operate the system from it |

**Scoring:** 25+ / 30 = genuinely interview-ready for primary target roles. 18–24 = close, revisit weak areas for 2–3 more weeks before heavy applying. Below 18 = don't rush applications yet; identify the specific gaps and go back to the relevant week.

### Final skill matrix

| Skill | Beginner | Practical | Interview Ready | Job Ready |
|---|---|---|---|---|
| Linux | Week 1 | Week 2 | Week 4 | Week 8+ |
| Networking | Week 2 | Week 3 | Week 4 | Week 8+ |
| Git | Week 3 | Week 4 | Week 6 | Week 10+ |
| Bash | Week 4 | Week 5 | Week 6 | Week 10+ |
| Python (light) | Ongoing (optional) | Ongoing | — | — |
| Docker | Week 4 | Week 5 | Week 6 | Week 10+ |
| CI/CD | Week 6 | Week 6 | Week 10 | Week 12 |
| AWS | Week 7 | Week 8 | Week 10 | Week 12 |
| Terraform | Week 9 | Week 10 | Week 12 | Month 4–5 |
| Kubernetes | Week 11 | Week 12 | Month 4 | Month 5–6 |
| Prometheus/Grafana | Week 12 | Week 12 | Month 4 | Month 5–6 |
| Security | Ongoing (woven throughout) | Week 10 | Month 4 | Month 5–6 |
| Troubleshooting | Ongoing | Week 8 | Week 12 | Month 4+ |
| AI-assisted DevOps | Week 1 (introduced) | Week 4 | Week 8 | Ongoing mastery |

*(This is a realistic pace estimate, not a guarantee — your own progress will vary based on time invested and prior background.)*

---

## MONTHS 4–12 ROADMAP

### Months 4–6 — Deepen and specialize
- Move Kubernetes toward a managed cluster (EKS) instead of local minikube/kind
- Learn Helm (packaging) once you're fully comfortable with raw manifests
- Deepen Terraform: remote state with locking, workspaces, environment promotion
- Add a real logging stack (basic ELK/Loki) alongside your existing Prometheus/Grafana setup
- Start applying seriously — treat weeks 1–2 of month 4 as "apply + interview," not "keep learning forever before applying"
- Attempt AWS Cloud Practitioner or Terraform Associate cert if it fits your target roles
- Contribute to a small open-source DevOps-adjacent project if possible (real collaboration experience)

### Months 6–12 — Toward a specialization
Pick a direction based on what you enjoyed most and where the market points you:
- **Toward DevOps Engineer (generalist):** deepen CI/CD patterns (canary/blue-green), multi-environment IaC, broaden AWS services (RDS, Lambda)
- **Toward Cloud Engineer:** go deeper on one cloud, pursue Associate/Professional-level certification, learn multi-account architecture
- **Toward SRE:** learn SLIs/SLOs and error budgets properly, study incident management frameworks, practice chaos engineering basics
- **Toward Platform Engineer:** learn Kubernetes Operators/CRDs, internal developer platforms, GitOps (Argo CD/Flux)
- **Toward DevSecOps:** deepen container/image scanning pipelines, learn a compliance framework, study IAM policy design more rigorously

Whichever direction you choose, keep applying and interviewing throughout — real interview feedback is itself a learning signal about where your gaps actually are.

---

## 23. REALISTIC EXPECTATIONS

**What can realistically be achieved in 3 months:** solid fundamentals across Linux, networking, Git, Docker, basic CI/CD, basic AWS, basic Terraform, and basic Kubernetes, plus 4 genuinely-understood portfolio projects and interview-level fluency in "what would you do if…" scenarios.

**What cannot realistically be mastered in 3 months:** deep AWS expertise across dozens of services, production-scale Kubernetes operations, true incident-response instincts (these come from real incidents), advanced security/compliance work, and the judgment that only comes from having broken something in production and cleaned it up under pressure.

**Why hands-on practice matters more than reading:** DevOps is a practice, not a body of trivia — the muscle memory of diagnosing a real `CrashLoopBackOff` at 11pm is what interviews (and jobs) actually test for.

**Why project quality matters more than project quantity:** one deeply-understood, well-documented project beats five shallow ones an interviewer can poke through in 30 seconds.

**Why troubleshooting matters:** almost every DevOps interview and every DevOps job is fundamentally about diagnosing problems under uncertainty — tool knowledge is necessary but not sufficient.

**Why fundamentals matter more than tool trends:** tools change every few years; Linux, networking, and systematic troubleshooting thinking don't.

**Why AI cannot replace engineering knowledge:** AI can be confidently wrong, can't see your actual environment, and won't be accountable when something breaks in production — you will be. Use it to accelerate learning, never to replace understanding.

**Why copying AI-generated infrastructure blindly is dangerous:** you won't be able to explain, secure, debug, or safely modify what you didn't actually understand when you built it — and in an interview or on the job, that gap shows immediately.

**Why production experience is different from personal projects:** real systems have real users, real consequences, legacy constraints, teammates with competing priorities, and incidents that happen at inconvenient times — no self-study project fully replicates that pressure, which is exactly why your first job is still a significant learning leap even after this roadmap.

**On the job search itself:** 3 months of disciplined study with strong projects makes you a credible, competitive candidate for trainee/junior roles — it does not guarantee an offer. Market conditions, competition, and how well you interview all matter. Keep building and keep applying in parallel; don't wait for "perfectly ready" before you start.
