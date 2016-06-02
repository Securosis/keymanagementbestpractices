Title: Evolving Encryption Key Management Best Practices for the Data Center

# Data centers and applications are changing; so is key management.

Cloud. DevOps. Microservices. Containers. Big Data. NoSQL.

We are in the midst of an IT transformation wave which is likely the most disruptive since we built the first data centers. One that's even more disruptive than the first days of the Internet, due to the convergence of multiple vectors of change. From the architectural disruptions of the cloud, to the underlying process changes of DevOps, to evolving Big Data storage practices, through NoSQL databases and the new applications they enable.

These have all changed how we use a foundational data security control: encryption. While encryption algorithms continue their steady evolution, encryption system *architectures* are being forced to change much faster due to rapid changes in the underlying infrastructure and the applications themselves. Security teams face the challenge of supporting all these new technologies and architectures, while maintaining and protecting existing systems.

Within the practice of data-at-rest encryption, key management is often the focus of this change. Keys must be managed and distributed in ever-more-complex scenarios, at the same time there is also increasing demand for encryption throughout our data centers (including cloud) and our application stacks.

This research highlights emerging best practices for managing encryption keys for protecting data at rest in the face of these new challenges. It also presents updated use cases and architectures for the areas where we get the most implementation questions. It is focused on data at rest, including application data; transport encryption is an entirely different issue, as is protecting data on employee computers and devices.

## How technology evolution affects key management

Technology is always changing, but there is a reasonable consensus that the changes we are experiencing now are coming faster than even the early days of the Internet. This is mostly because we see a mix of both architectural and process changes within data centers and applications. The cloud, increased segregation, containers, and micro services, all change architectures; while DevOps and other emerging development and operations practices are shifting development and management practices. Better yet (or worse, depending on your perspective), all these changes mix and reinforce each other.

Enough generalities. Here are the top trends we see impacting data-at-rest encryption:

* **Cloud Computing:** The cloud is the single most disruptive force affecting encryption today. It is driving very large increases in encryption usage, as organizations shift to leverage shared infrastructure. We also see increased *internal* use of encryption due to increased awareness, hybrid cloud deployments, and in preparation for moving data into the cloud.

	The cloud doesn't only affect encryption adoption -- it also fundamentally influences architecture. You cannot simply move applications into the cloud without re-architecting (at least not without seriously breaking things -- and trust us, we see this every day). This is especially true for encryption systems and key management, where integration, performance, and compliance all intersect to affect practice.
* **Increased Segmentation:** We are far past the days when flat data center architectures were acceptable. The cloud is massively segregated by default, and existing data centers are increasingly adding internal barriers. This affects key management architectures, which now need to support different distribution models without adding management complexity.
* **Microservice architectures:** Application architectures themselves are also becoming more compartmentalized and distributed as we move away from monolithic designs into increasingly distributed, and sometimes ephemeral, services. This again increases demand to distribute and manage keys at wider scale without compromising security.
* **Big Data and NoSQL:** Big data isn't just a catchphrase -- it encompasses a variety of very real new data storage and processing technologies. NoSQL isn't *necessarily* big data, but has influenced other data storage and processing as well. For example, we are now moving massive amounts of data out of relational databases into distributed file-system-based repositories. This further complicates key management, because we need to support distributed data storage and processing on larger data repositories than ever before.
* **Containers:** Containers continue the trend of distributing processing and storage (noticing a theme?), on an even more ephemeral basis, where containers might appear in microseconds and disappear in minutes, in response to application and infrastructure demands.
* **DevOps:** To leverage these new changes and increase effectiveness and resiliency, DevOps continues to emerge as a dominant development and operational framework -- not that there is any single definition of DevOps. It is a philosophy and collection of practices that support extremely rapid change and extensive automation. This makes it essential for key management practices to integrate, or teams will simply move forward without support.

These technologies and practices aren't mutually exclusive. It is extremely common today to build a microservices-based application inside containers running at a cloud provider, leveraging NoSQL and Big Data, all managed using DevOps. Encryption may need to support individual application services, containers, virtual machines, and underlying storage, which might connect back to an existing enterprise data center via a hybrid cloud connection.

It isn't always this complex, but sometimes it is. So key management practices are changing to keep pace, so they can provide the right key, at the right time, to the right location, without compromising security, while still supporting traditional technologies.

# Best Practices

If there is one thread tying together all of the trends impacting data centers and how we build applications, it's "distributed". We have greater demand for encryption in more locations in our stacks, which now span physical environments, virtual environments, and increasing barriers even within our traditional environments. 

Some of the best practices we will highlight are ones long familiar to anyone responsible for enterprise encryption. Separation of duties, key rotation, and meeting compliance requirements never really change. Even others are familiar, but now take on a new priority thanks to all the trends reforming our data centers. Providing key management as a service and dispersing and integrating into required architectures aren't technically new, but are certainly in greater demand. Then there are the practices that might not have made the list, such as supporting APIs and distributed architectures (potentially spanning physical and virtual appliances).

As you will see, the name of the game is consolidating for consistency and control, while distributing to support diverse encryption needs, architectures, and project requirements.

Lastly, before we jump into the recommendations, remember our focus. This research is for enterprise data centers, including virtualization and cloud computing. There are plenty of other encryption use cases out there that don't necessarily require everything we discuss, although you can likely still pick up a few good ideas.

## Build a key management service

Supporting multiple projects with different needs can easily result in a bunch of key management silos using different tools and technologies that become difficult to support. One for application data, another for databases, another for backup tapes, another for SANs, and maybe even multiple different deployments for the same coverage as individual teams picked and chose their own technologies. This is especially true in the agile, project-based world of cloud, microservices, and containers. Technically there's nothing inherently wrong with these silos assuming they are all properly managed, but odds are they won't be. Plus, this can increase costs due to overlapping technologies.

Overall we tend to recommend building centralized security services to support the organization, and this most definitely applies to encryption. Let a smaller team of security and product pros manage what they are best at and support everyone else, rather than merely issuing policy requirements that slow down projects.

For this to work the central service needs to be agile and responsive, ideally with internal Service Level Agreements to keep everyone accountable. Projects request encryption support, and the team managing the central service determines the best way to integrate, meet security and compliance requirements, then provides the needed access and technical support to make it happen.

This allows you to consolidate and better manage your key management tools, while being able to maintain security and compliance requirements such as audit and separation of duties. Whatever tool(s) you do select clearly need to support your various distributed requirements. The last thing you want to do is centralize, but put in place processes, tools, and requirements that impeded the ability of projects to meet their own goals.

And don't focus so exclusively on new projects and technologies that you forget about what's already in place. Our advice isn't merely for microservice, container-based, cloud-hosted projects, but applies equally to backup tapes and SAN encryption.

## Centralize, but disperse and support distributed needs

Once you establish a centralized service, now you need to support distributed access. There are two primary approaches, but we really only recommend one for most organizations:

* *Allow access from anywhere*. In this model you position the key manager in a location that is accessible from wherever it might be needed. Typically organizations select this option when they want to only maintain a single key manager (or cluster). It was a common architecture in traditional data centers, but isn't well-suited for the kinds of situations we increasingly see today.
* *Distributed architecture*. In this model you maintain a core "root of trust" key manager (which can, again, be a cluster), but then you position distributed key managers that tie back to the central service. These can be a mix of physical/virtual appliances or servers. Typically they only hold the keys for the local application, device, etc. that needs them (especially when using virtual appliances or software on a shared service). Rather than connecting back for every key operation, the local key manager handles those while synchronizing back to the central root of trust. 

Why distribute key managers that still need a connection back home? It allows you to support greater local administrative control and meet local performance requirements. It also keeps applications and services up and running if there is some sort of a network outage or other block back to the central service. This model provides a great balance between security and performance.

For example, you could support a virtual appliance in a cloud project, physical appliances in backup data centers, and back up keys used within your cloud provider with their built-in encryption service.

Also, it provides flexibility if you need different technologies for the distributed projects. The local key manager doesn't necessarily need to have to be the exact same product as the central one, as long as they can communicate and both meet security and compliance requirements. We have seen architectures where the central service is a cluster of Hardware Security Module appliances (with key management features) that support distributed HSMs, virtual appliances, and even custom software.

The biggest potential obstacle is providing safe, secure access back to the core. Architecturally you can usually manage this with some bastion systems to support key exchanges without opening the core to the Internet. There may still be some use cases where you can't necessarily tie everything together, but that should be your last option.

## Be flexible; use the right tool for the right job

Building on the previous recommendation, you don't necessarily need to force every project to use a single tool. One of the great things about key management is that modern systems support a number of standards for intercommunication. And, when you really get down to it, an encryption key is merely a chunk of text, and not usually a very large one.

With encryption systems the keys and the encryption engine don't need to be the exact same product. Even your remote key manager doesn't need to be the same as the central service if you need something different for that particular project.

We've seen large encryption projects fail due to trying to shoehorn everything into a more-monolithic stack. You increase your chances for success by allowing some flexibility on the exact remote tools used as long as they meet your security requirements. This is especially true for the encryption engines that perform the actual crypto operations.

## Provide APIs, SDKs, and toolkits

Even off the shelf encryption engines sometimes ship with less than ideal defaults, and can easily be used incorrectly. Building a key management service isn't merely about creating a central key manager, it also means providing the fundamental hooks to enable projects, and the processes and guidance to ensure they are able to get up and running quickly and securely.

* *Application Programming Interfaces*: Most key management tools already support APIs and this should be a selection requirement. Make sure you support REST APIs which are particularly ubiquitous in cloud and containers. SOAP APIs are considered pretty burdensome these days. 
* *Software Development Kits*: SDKs are pre-built code modules that allow rapid integration into custom applications. Provide SDKs for common programming languages that are compatible with your key management service/products. if possible, you can even pre-configure them to meet your encryption requirements and integrate with the service. 
* *Toolkits*: A toolkit includes all the technical pieces a team needs to get started. It can include SDKs, pre-configured software agents, configuration files, and anything else a project could need to integrate encryption into everything from a new application, to an older tape backup system.

## Provide templates and recommendations, not just standards and requirements

All too often security sends out requirements, but doesn't provide specific instructions to meet those requirements. One of the advantages of standardization around a smaller set of tools is you can then provide  the detailed recommendations, instructions, and templates to meet those requirements.

The more detail you can provide the better. We recommend literally creating instructions documents for how to use all approved tools, even with screenshots, to meet encryption needs and integrate with the key management service. Make them easily available, even through code repositories to better integrate with application developers. On the operations side, include them not only for programming and APIs, but for software agents and integration into supported storage repositories and backup systems.

If a project comes up where there isn't a toolkit or existing recommendations that fit, build them with that project team and then add the new guidance into your central repository. This dramatically speeds up encryption initiatives for existing and new platforms.

## Meet core security requirements

So far we've focused more on newer requirements to meet evolving data center architectures and the impact of cloud and new application design patterns, but all the old key management practices still apply:

* Enforce separation of duties: Implement multiple levels of administrators. Ideally require dual-authority for operations directly impacting key security and other major administrative functions.
* Support key rotation: Ideally key rotation shouldn't create downtime. This typically means a combination of support in the key manager, plus proper configuration within the encryption engines and agents in use.
* Enable usage logs for audit, including purpose codes: Logs may be required for compliance, but are also a really good security idea. Purpose codes tell you why a key was requested, not just who or when.
* Support standards: Whatever you use for key management must support both major encryption standards and key exchange/management standards. Don't rely on fully proprietary systems that will overly limit your choices.
* Understand the role of FIPS, the different flavors, and ensure you meet your requirements: FIPS 140-2 is the most commonly accepted standard for cryptographic modules and systems. Many products advertise they are FIPS compliant (which is often a requirement for other compliance needs, like PCI). However, FIPS is a graded standard with different levels ranging from a software module, to plugin cards, to a fully tamper resistant dedicated appliance. Understand your FIPS needs and don't assume that just because something advertises itself as an "appliance" that the *entire appliance* is FIPS certified, it could just be the software. not that you always need the highest level of assurance, but you do need to know your requirements and then ensure the tool you use actually meets those requirements.

There are many more technical best practices beyond the scope of this research, but the core advice that might be different that what you've seen in the past is:

* Provide key management as a service to meet diverse encryption needs.
* Be able to support distributed architectures and a range of use cases.
* Be flexible on tool choice, then provide the technical components and clear guidance on how to properly use the tools and integrate them into your key management program.
* Don't neglect core security requirements.

In our next section we will start looking at specific use cases, some of which we've already hinted at.



