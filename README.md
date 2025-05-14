# Web Infrastructure Design

This repository contains a set of infrastructure design tasks, focusing on how to build, scale, secure, and monitor modern web server environments.

Each task builds upon the previous one, evolving from a simple single-server stack into a distributed and scalable infrastructure ready for production challenges.

---

## Task 0: Simple Web Stack

> A first dive into infrastructure: one server does it all.

- 1 server hosts:
  - A web server (Nginx)
  - An application server
  - The application codebase
  - A MySQL database
- Domain `www.foobar.com` resolved via a DNS A record to IP `8.8.8.8`.

You’ll explain:
- What each component does (server, DNS, web/app server, DB)
- How a single server handles requests
- The limits of this setup (SPOF, maintenance downtime, no scalability)

➡️ See: `0-simple_web_stack`

---

## Task 1: Distributed Web Infrastructure

> Time to split the workload across multiple machines.

- A load balancer (HAProxy) distributes traffic using **Round Robin**
- 2 identical backend servers (each with web server, app server, app files, and database)
- A MySQL **Primary-Replica cluster** for better read/write separation

You’ll explain:
- The purpose of load balancing
- Active-Active vs Active-Passive setups
- How Primary-Replica DB replication works
- The new SPOFs (like the single load balancer)

➡️ See: `1-distributed_web_infrastructure`

---

## Task 2: Secured and Monitored Web Infrastructure

> Your infra is now protected and observable — no more blind spots.

New components:
- Firewalls on each machine
- An SSL certificate to serve `https://www.foobar.com`
- Monitoring agents on all servers

You’ll explain:
- What HTTPS is and why SSL termination at the load balancer has trade-offs
- The purpose of monitoring and how agents collect data (QPS, system health, logs)
- New issues introduced (unencrypted internal traffic, monitoring limitations)

➡️ See: `2-secured_and_monitored_web_infrastructure`

---

## Task 3: Scale Up

> Splitting the roles to scale each part independently.

New architecture:
- A second load balancer (clustered with the first)
- A dedicated set of servers for:
  - Web servers (Nginx) – static content
  - App servers (Flask/PHP/etc.) – logic
  - Database (MySQL) – storage

You’ll explain:
- The difference between a web server and an app server
- Why separating roles allows better performance and scalability
- Why scaling horizontally needs architectural clarity

➡️ See: `3-scale_up`

---

## Bonus: Vocabulary Highlights

- **SPOF (Single Point of Failure)**: a component that, if it fails, brings down the whole system
- **Round Robin**: a basic traffic distribution algorithm
- **Primary-Replica DB**: separation of writes (Primary) and reads (Replica)
- **SSL Termination**: decrypting HTTPS at the load balancer
- **QPS (Queries Per Second)**: metric used to measure incoming traffic volume

---

## Author

This project is part of the Holberton curriculum
