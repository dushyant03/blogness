+++
title = 'Kubernetes an emotion'
date = 2025-05-21T15:20:38+01:00
draft = false
+++

Kubernetes nowadays is a great buzzword among the software community. Actually, it has been for a while now, but not everyone feels the same about it — especially when it comes to its purpose and how it can evolve an architecture in both the wrong and the right way. In this blog, I am going to pen down what I thought, think, and will think about Kubernetes.

The first time I heard the word "Kubernetes" was way back in 2017, when I was working for a Bangalore-based startup. There was a special KPI in that startup around using innovation in your daily work, and someone in the team had heard about this tool called Kubernetes, developed by Google, now in the market as the next big thing. At that time, I was still heavily immersed in the legacy AWS world — EC2, launch templates, and autoscaling groups (still used to this day). It was also a painful time of doing things manually via the AWS console, with a mixture of CloudFormation. We never really got to explore Kubernetes back then or while I was in that organization.

Cut to 1.5 years later, I was exploring opportunities in Europe and had just started applying to DevOps roles in the Netherlands and Germany. In my resume, I mentioned that I had started self-learning Kubernetes and Terraform. I did a few Pluralsight and Udemy courses on Kubernetes. I'll be honest — it all went over my head.

By then, I had received some assignments from the companies I was applying to. I used Docker and Docker Compose to build and deploy applications for those assignments. While doing that, I kept trying to learn more about Kubernetes in simple terms through YouTube and other platforms. Then came an assignment from a startup in Amsterdam that required me to deploy a certain API on Kubernetes. I was excited initially, as I was finally going to apply what little I knew and get it validated. With the help of a friend who was good with Kubernetes, I deployed the assignment on Minikube using a Deployment, Service, and port-forwarding to access the API. I won't go into too much detail, but they liked my submission, and soon enough I was offered a job in Amsterdam. The rest is history — the biggest move of my life from India to Western Europe.

Now in Amsterdam, living my dream in this new organization, I had to start working with Kubernetes in a production environment, managing at least two clusters with a multitude of applications deployed. This was on GKE, on Google Cloud, so I needed to understand how the clusters were deployed, how to deploy applications to them, and how to maintain everything.

One of my first tasks was to migrate a certain set of applications from one GKE cluster to another. We were splitting up teams and the applications they managed, so each team was going to have their own two GKE clusters (Dev and Prod) and manage the apps deployed on those clusters. This was actually a fun first task because I got to understand the full lifecycle of an application deployed in Kubernetes — from the Dockerfile to curling the endpoint. I had to do a lot of after-work sessions with myself and seek answers online to make sense of it all — all from a hostel in central Amsterdam. Fortunately, within a week I was able to migrate all the applications. It felt like Kubernetes had accepted me — and I had accepted it. This was the moment I knew I loved this technology and wanted to work with it for as long as I could. After that, I worked very closely with GKE for over a year and loved every moment.

Later, in my other gigs, I got to work on EKS — the managed Kubernetes service from AWS. To be very honest, I hated EKS in the beginning, especially coming from GKE. Even though Google Cloud isn’t on par with AWS in many areas, I feel they really nailed GKE. The sheer ease of setup and usage of GKE over any other cloud provider was amazing. Nonetheless, I worked on many projects as a consultant, helping clients transition from various compute solutions to EKS or GKE. During these experiences, I often had to justify why Kubernetes was the right answer — and sometimes explain why it wasn’t.

Let me highlight why Kubernetes sometimes is not the right answer:

- When trying to use Kubernetes the hard way — deploying and managing control planes and worker nodes in an on-prem environment. Teams spend a lot of effort maintaining these clusters, and I’ve heard horror stories of unfixable cluster failures.
- When you have only a small set of applications that could easily be managed via virtual machines or a simpler service like ECS.
- When you don’t have a dedicated infrastructure team. Some companies expect their backend teams to manage infrastructure — I would suggest not using Kubernetes in that case. It requires effort to set up and maintain correctly.- 
- When there's a lack of knowledge of core Kubernetes concepts within the team. It takes years of production experience to set up, maintain, and troubleshoot clusters effectively. The learning curve is steep.
- Most importantly — Kubernetes is not the answer just because everyone else is doing it. Always weigh the pros and cons before making the jump.

Now, why Kubernetes is the right answer:
- When you have a multitude of applications deployed on virtual machines that need to scale frequently via autoscaling.
- When you have a high-traffic platform that needs to scale quickly based on demand.
- When you want your compute environment to be stateless — treating servers like cattle, not pets. Rather than troubleshooting a broken instance, you can just redeploy the app on a fresh machine.
- When you can leverage powerful tools that make Kubernetes even more effective — like Helm, Karpenter, External-DNS, External-Secrets, load balancer controllers, ingress controllers, and many more.
- When you want built-in security best practices while deploying and managing clusters.
- When you want access to a strong, supportive community.

In conclusion, I personally love Kubernetes. Through the various projects I've worked on, I’ve learned a lot about deploying container-based applications using Kubernetes. I always look for companies that are already using Kubernetes or are planning to migrate to it — it’s more than just a technology for me. It’s an emotion.