+++
title = 'Atlantis - boon or bane'
date = 2025-05-17T15:20:38+01:00
draft = false
+++

Back to writing another blog after a really long time. A lot has happened in the last year, which kept me away from penning down the ideas and thoughts I’ve had during that period. Today, I made some time to keep the blog post somewhat alive.

I’ve been working at my new job for the past year and have been very involved in improving the overall infrastructure in the organization. Out of the many things that were done, one major change I introduced was Kubernetes. As most techies know, Kubernetes comes with both significant benefits and some limitations. Having had good exposure to managed Kubernetes environments, I wanted to introduce it here as well. This post isn’t about Kubernetes itself, but rather about how we deploy applications on Kubernetes—specifically, on a private Kubernetes cluster.

To give some highlevel context, we set up a private Kubernetes cluster in EKS entirely via Terraform. We started with creating the networking base and then used that to deploy our EKS cluster—all using Terraform and Terraform modules. Initially, the Terraform code was applied manually from my local Mac, as I was the only one deploying and applying changes to our EKS environment. Once we had a robust enough Dev environment, we chose a backend application to deploy and eventually migrate to EKS. This was done using a combination of Helm, Docker, and Terraform—in simple terms, deploying the Helm charts using Terraform (again, all from my Mac).

I knew from the beginning that a time would come when we’d need to automate the deployment of Helm charts via Terraform, especially since our plan was for developers to manage and deploy their own applications. Around this time, priorities in the organization shifted, and there was increased interest in Kubernetes. We were given about two weeks to provide a solution to automate the deployment of the backend application on private EKS clusters.

This is where the real story begins. Our small DevOps team made a quick decision to explore Atlantis. While GitHub Private Runners was our preferred choice, we realized setting up Atlantis would be faster and sufficient for the time being. So, we scrambled to deploy Atlantis in our EKS clusters, hooked it up to GitHub via GitHub Apps, and got atlantis plan and atlantis apply working in our repositories. To briefly explain, Atlantis is a pull-request-based deployment tool, meaning you can run Terraform code via comments in a PR.

After ample testing within the DevOps team, we presented the workflow to the developers, who were now expected to use it to deploy to our Kubernetes environments. On deployment day, I, being the flag bearer of Atlantis and the single point of contact—was bombarded with questions from multiple developers, all trying to understand how Atlantis actually worked and why it felt so complicated. A few fundamental issues emerged:

- Developers would merge the PRs and then try to deploy via Atlantis, missing the core concept of PR-based deployments.
- The combination of GitHub Actions (for building and pushing Docker images) and Atlantis caused confusion.
- Atlantis makes a commit with the new image tag in the Terraform files, leading to merge conflicts in PRs.
- Empty PRs were created just to trigger Atlantis deployments.
- The conversation section in PRs became cluttered with massive Atlantis plan outputs, making it hard to make sense of anything.

My plan was to continue using Atlantis until we had the bandwidth to properly set up GitHub Private Runners and build a smoother transition. But, of course, that didn’t happen. The dev teams had mixed feelings about Atlantis. Instead of making them more independent, it made them even more dependent on the DevOps team. I found myself handling deployments for them more often than not.

In conclusion, Atlantis is a great tool—when used within infrastructure teams—to collaborate on deploying Terraform code. It's fundamentally an infrastructure tool rather than a cross-team collaborative one, and it requires at least a basic understanding of Terraform to be used effectively. I still really like Atlantis, but we’re moving away from it for good reason.
