# Static Website Hosting with Amazon S3, CloudFront & Route 53

Host a secure, scalable, and cost-effective static website on AWS using Amazon S3, CloudFront, Route 53, and AWS Certificate Manager (ACM).

## Project Overview

This project demonstrates how to deploy a secure, production-ready static website on AWS without using a traditional web server.

The website is hosted in an Amazon S3 bucket and distributed globally through Amazon CloudFront. Amazon Route 53 manages DNS, while AWS Certificate Manager (ACM) provides a free SSL certificate for HTTPS encryption.

This architecture is ideal for portfolios, landing pages, business websites, and documentation sites because it is secure, highly available, scalable, and cost-effective.

## Live Demo

**EduKare:** https://edukare.edwardfabunmi.online


## Table of Contents

* [Project overview](Doc/01-project-overview.md)
- [Architecture](Doc/02-architecture.md)
- [AWS Services Used](Doc/03-aws-services-used.md)
- [Architecture Workflow](Doc/04-architecture-workflow.md)
- [Prerequisites](Doc/05-prerequisites.md)
- [Deployment Guide](Doc/06-deployment-guide.md)
- [Security Features](Doc/07-security-features.md)
- [Estimated Monthly Cost](Doc/08-estimated-monthly-cost.md)
- [Lessons Learned](Doc/09-lessons-learned.md)
- [Future Improvements](Doc/10-future-improvements.md)
- [Author](Doc/12-author.md)

## Project Objective

The objective of this project is to design and deploy a secure, scalable, and cost-effective static website hosting solution on AWS using Amazon S3, Amazon CloudFront, Amazon Route 53, and AWS Certificate Manager (ACM).

The project demonstrates how to leverage AWS managed services to deliver a highly available website with HTTPS encryption, low latency through global content delivery, secure access using Origin Access Control (OAC), and custom domain integration while following AWS security best practices.

## Project Deliverables

Upon completion of this project, the following deliverables were achieved:

- Successfully deployed a static website on Amazon S3.
- Configured Amazon CloudFront to deliver content through global edge locations.
- Implemented HTTPS using AWS Certificate Manager (ACM).
- Connected a custom domain using Amazon Route 53.
- Secured the S3 bucket with Origin Access Control (OAC) to prevent direct public access.
- Configured DNS records for both the root domain.
- Improved website performance through CloudFront content caching.
- Documented the complete deployment process with architecture diagrams and implementation steps.
- Created a production-style AWS project suitable for portfolio and learning purposes.
