Title: Evolving Encryption Key Management Best Practices for the Data Center

# Data centers and applications are changing; so is key management.

Cloud. DevOps. Microservices. Containers. Big Data. NoSQL.

We are in the midst of an IT transformation wave which is likely the most disruptive since we built the first data centers. One that's even more disruptive than the first days of the Internet, due to the convergence of multiple vectors of change. From the architectural disruptions of the cloud, to the underlying process changes of DevOps, to evolving Big Data storage practices, through NoSQL databases and the new applications they enable.

These have all changed how we use a foundational data security control: encryption. While encryption algorithms continue their steady evolution, encryption system *architectures* are being forced to change much faster due to rapid changes in the underlying infrastructure and the applications themselves. Security teams face the challenge of supporting all these new technologies and architectures, while maintaining and protecting existing systems.

Within the practice of data-at-rest encryption, key management is often the focus of this change. Keys must be managed and distributed in ever-more-complex scenarios, at the same time there is also increasing demand for encryption throughout our data centers (including cloud) and our application stacks.

This research highlights the emerging best practices for managing encryption keys for protecting data at rest in the face of these new challenges. It also presents updated use cases and architectures for those areas where we see the most implementation questions. It's completely focused on data at rest, including application data; transport encryption is an entirely different issue, as is protecting data on employee computers and devices.

## How technology evolution affects key management

Technology is always changing, but there is a reasonable consensus that the changes we are experiencing now are coming faster than even the early days of the Internet. This is mostly because we see a mix of both architectural and process changes within data centers and applications. The cloud, increased segregation, containers, and micro services, all change architectures; while DevOps and other emerging development and operations practices are shifting development and management practices. Better yet (or worse, depending on your perspective), all these changes mix and reinforce each other.

Enough generalities. Here are the top trends we see impacting data-at-rest encryption:

* **Cloud computing:** The cloud is the single most disruptive force affecting encryption today. It is driving very large increases in encryption usage, as organizations shift to leverage shared infrastructure. We also see increased *internal* use of encryption due to increased awareness, hybrid cloud deployments, and in preparation for moving data into the cloud.

	The cloud doesn't only affect encryption adoption -- it also fundamentally influences architecture. You cannot simply move applications into the cloud without re-architecting (at least not without seriously breaking things -- and trust us, we see this every day). This is especially true for encryption systems and key management, where integration, performance, and compliance all intersect to affect practice.
* **Increased segmentation:** We are far past the days when flat data center architectures were acceptable. The cloud is massively segregated by default, and existing data centers are increasingly adding internal barriers. This affects key management architectures, which now need to support different distribution models without adding management complexity.
* **Microservice architectures:** Application architectures themselves are also becoming more compartmentalized and distributed as we move away from monolithic designs into increasingly distributed, and sometimes ephemeral, services. This again increases demand to distribute and manage keys at wider scale without compromising security.
* **Big data and NoSQL:** Big data isn't just a catchphrase -- it encompasses a variety of very real new data storage and processing technologies. NoSQL isn't *necessarily* big data, but has influenced other data storage and processing as well. For example, we are now moving massive amounts of data out of relational databases into distributed file-system-based repositories. This further complicates key management, because we need to support distributed data storage and processing on larger data repositories than ever before.
* **Containers:** Containers continue the trend of distributing processing and storage (noticing a theme?), on an even more ephemeral basis, where containers might appear in microseconds and disappear in minutes, in response to application and infrastructure demands.
* **DevOps:** To leverage these new changes and increase effectiveness and resiliency, DevOps continues to emerge as a dominant development and operational framework -- not that there is any single definition of DevOps. It is a philosophy and collection of practices that support extremely rapid change and extensive automation. This makes it essential for key management practices to integrate, or teams will simply move forward without support.

These technologies and practices aren't mutually exclusive. It is extremely common today to build a microservices-based application inside containers running at a cloud provider, leveraging NoSQL and Big Data, all managed using DevOps. Encryption may need to support individual application services, containers, virtual machines, and underlying storage, which might connect back to an existing enterprise data center via a hybrid cloud connection.

It isn't always this complex, but sometimes it is. Key management practices are changing to keep pace, so they can provide the right key, at the right time, to the right location, without compromising security, while still supporting traditional technologies.

# Best Practices

If there is one thread tying together all the current trends influencing data centers and how we build applications, it's *distribution*. We have greater demand for encryption in more locations in our application stacks -- which now span physical environments, virtual environments, and increasing barriers even within our traditional environments.

Some of the best practices we will highlight have long been familiar to anyone responsible for enterprise encryption. Separation of duties, key rotation, and meeting compliance requirements have been on the checklist for a long time. Others are familiar, but have new importance thanks changes occurring in data centers. Providing key management as a service, and dispersing and integrating into required architectures aren't technically new, but they are in much greater demand than before. Then there are the practices which might not make the list, such as supporting APIs and distributed architectures (potentially spanning physical and virtual appliances).

As you will see, the name of the game is consolidation for consistency and control; simultaneous with distribution to support diverse encryption needs, architectures, and project requirements.

But before we jump into recommendations, keep our focus in mind. This research is for enterprise data centers, including virtualization and cloud computing. There are plenty of other encryption use cases out there which don't necessarily require everything we discuss, although you can likely still pick up a few good ideas.

## Build a key management service

Supporting multiple projects with different needs can easily result in a bunch of key management silos using different tools and technologies, which become difficult to support. One for application data, another for databases, another for backup tapes, another for SANs, and possibly even multiple deployments for the same functions, as individual teams pick and choose their own preferred technologies. This is especially true in the project-based agile world of the cloud, microservices, and containers. There's nothing inherently wrong with these silos, assuming they are all properly managed, but that is unfortunately rare. And overlapping technologies often increase costs.

Overall we tend to recommend building centralized security services to support the organization, and this definitely applies to encryption. Let a smaller team of security and product pros manage what they are best at and support everyone else, rather than merely issuing policy requirements that slow down projects or drive them underground.

For this to work the central service needs to be agile and responsive, ideally with internal Service Level Agreements to keep everyone accountable. Projects request encryption support; the team managing the central service determines the best way to integrate, and to meet security and compliance requirements; then they provide access and technical support to make it happen.

This enables you to consolidate and better manage key management tools, while maintaining security and compliance requirements such as audit and separation of duties. Whatever tool(s) you select clearly need to support your various distributed requirements. The last thing you want to do is centralize but establish processes, tools, and requirements that interfere with projects meeting their own goals.

And don't focus so exclusively on new projects and technologies that you forget about what's already in place. Our advice isn't merely for projects based on microservices containers, and the cloud -- it applies equally for backup tapes and SAN encryption.

## Centralize but disperse, and support distributed needs

Once you establish a centralized service you need to support distributed access. There are two primary approaches, but we only recommend one for most organizations:

* **Allow access from anywhere:** In this model you position the key manager in a location accessible from wherever it might be needed. Typically organizations select this option when they want to only maintain a single key manager (or cluster). It was common in traditional data centers, but isn't well-suited for the kinds of situations we increasingly see today.
* **Distributed architecture:** In this model you maintain a core "root of trust" key manager (which can, again, be a cluster), but then you position distributed key managers which tie back to the central service. These can be a mix of physical and virtual appliances or servers. Typically they only hold the keys for the local application, device, etc. that needs them (especially when using virtual appliances or software on a shared service). Rather than connecting back to complete every key operation, the local key manager handles those while synchronizing keys and configuration back to the central root of trust.

Why distribute key managers which still need a connection back home? Because they enable you to support greater local administrative control and meet local performance requirements. This architecture also keeps applications and services up and running in case of a network outage or other problem accessing the central service. This model provides an excellent balance between security and performance.

For example you could support a virtual appliance in a cloud project, physical appliances in backup data centers, and backup keys used within your cloud provider with their built-in encryption service.

This way you can also support different technologies for distributed projects. The local key manager doesn't necessarily need to be the exact same product as the central one, so long as they can communicate and both meet your security and compliance requirements. We have seen architectures where the central service is a cluster of Hardware Security Modules (appliances with key management features) supporting a distributed set of HSMs, virtual appliances, and even custom software.

The biggest potential obstacle is providing safe, secure access back to the core. Architecturally you can usually manage this with some bastion systems to support key exchange, without opening the core to the Internet. There may still be use cases where you cannot tie everything together, but that should be your last option.

## Be flexible: use the right tool for the right job

Building on our previous recommendation, you don't need to force every project to use a single tool. One of the great things about key management is that modern systems support a number of standards for intercommunication. And when you get down to it, an encryption key is merely a chunk of text -- not even a very large one.

With encryption systems, keys and the encryption engine don't need to be the same product. Even your remote key manager doesn't need to be the same as the central service if you need something different for that particular project.

We have seen large encryption projects fail because they tried to shoehorn everything into a single monolithic stack. You can increase your chances for success by allowing some flexibility in remote tools, so long as they meet your security requirements. This is especially true for the encryption engines that perform actual crypto operations.

## Provide APIs, SDKs, and toolkits

Even off-the-shelf encryption engines sometimes ship with less than ideal defaults, and can easily be used incorrectly. Building a key management service isn't merely creating a central key manager -- you also need to provide hooks to support projects, along with processes and guidance to ensure they are able to get up and running quickly and securely.

* **Application Programming Interfaces:** Most key management tools already support APIs, and this should be a selection requirement. Make sure you support RESTful APIs, which are particularly ubiquitous in the cloud and containers. SOAP APIs are considered burdensome these days.
* **Software Development Kits:** SDKs are pre-built code modules that allow rapid integration into custom applications. Provide SDKs for common programming languages compatible with your key management service/products. If possible you can even pre-configure them to meet your encryption requirements and integrate with your service.
* **Toolkits:** A toolkit includes all the technical pieces a team needs to get started. It can include SDKs, preconfigured software agents, configuration files, and anything else a project might need to integrate encryption into anyything from a new application to an old tape backup system.

## Provide templates and recommendations, not just standards and requirements

All too often security sends out requirements, but fails to provide specific instructions for meeting those requirements. One of the advantages of standardization around a smaller set of tools is that you can provide detailed recommendations, instructions, and templates to satisfy requirements.

The more detail you can provide the better. We recommend literally creating instructional documents for how to use all approved tools, likely with screenshots, to meet encryption needs and integrate with your key management service. Make them easily available, perhaps through code repositories to better support application developers. On the operations side, include them not only for programming and APIs, but for software agents and integration into supported storage repositories and backup systems.

If a project comes up which doesn't fit any existing toolkit or recommendations, build them with that project team and add the new guidance to your central repository. This dramatically speeds up encryption initiatives for existing and new platforms.

## Meet core security requirements

So far we have focused on newer requirements to meet evolving data center architectures, the impact of the cloud, and new application design patterns; but all the old key management practices still apply:

* **Enforce separation of duties:** Implement multiple levels of administrators. Ideally require dual authorities for operations directly impacting key security and other major administrative functions.
* **Support key rotation:** Ideally key rotation shouldn't create downtime. This typically requires both support in the key manager and configuration within encryption engines and agents.
* Enable usage logs for audit, including purpose codes: Logs may be required for compliance, but are also key for security. Purpose codes tell you why a key was requested, not just by who or when.
* **Support standards:** Whatever you use for key management must support both major encryption standards and key exchange/management standards. Don't rely on fully proprietary systems that will overly limit your choices.
* **Understand the role of FIPS and its different flavors, and ensure you meet your requirements:** FIPS 140-2 is the most commonly accepted standard for cryptographic modules and systems. Many products advertise FIPS compliance (which is often a requirement for other compliance, such as PCI). But FIPS is a graded standard with different levels ranging from a software module, to plugin cards, to a fully tamper-resistant dedicated appliance. Understand your FIPS requirements, and if you evaluate a "FIPS certified" 'appliance', don't assume the *entire* appliance is certified -- it might be only the software, not the whole system. You may not always need the highest level of assurance, but start by understanding your requirements, and then ensure your tool actually meets them.

There are many more technical best practices beyond the scope of this research, but the core advice that might differ from what you have seen in the past is:

* Provide key management as a service to meet diverse encryption needs.
* Be able to support distributed architectures and a range of use cases.
* Be flexible on tool choice, then provide technical components and clear guidance on how to properly use tools and integrate them into your key management program.
* Don't neglect core security requirements.

In our next section we will start looking at specific use cases, some of which we have already hinted at.

# Use Cases

Now that we've discussed best practices, it's time to cover common use cases. Well, mostly common -- one of our goals for this research is to highlight emerging practices, so a couple of our use cases cover newer data-at-rest key management scenarios, while the rest are more traditional options.

## Traditional Data Center Storage

It feels a bit weird to use the word 'traditional' to describe a data center, but people give us strange looks when we call the most widely deployed storage technologies 'legacy'. We'd say "old school", but that sounds a bit too retro. Perhaps we should just say "big storage stuff that doesn't involve the cloud or other weirdness".

We typically see three major types of data storage encrypted at rest in traditional data centers: SAN/NAS, backup tapes, and databases. We also occasionally we also see file servers encrypted, but they are in the minority. Each of these is handled slightly differently, but normally one of three 'meta-architectures' is used:

* **Silos:** Some storage tools include their own encryption capabilities, managed within the silo of the application/storage stack. For example a backup tape system with built-in encryption. The keys are managed by the tool within its own stack. In this case an external key manager isn't used, which can lead to a risk of application dependency and key loss, unless it's a very well-designed product.
* **Centralized key management:** Rather than managing keys locally, a dedicated central key management tool is used. Many organizations start with silos, and later integrate them with central key management for advantages such as improved separation of duties, security, auditability, and portability. Increasing support for [KMIP and the PKCS 11 standards](https://en.wikipedia.org/wiki/Key_Management_Interoperability_Protocol) enables major products to leverage remote key management capabilities, and exchange keys.
* **Distributed key management:** This is very common when multiple data centers are either actively sharing information or available for disaster recovery (hot standby). You *could* route everything through a single key manager, but this single point of failure would be a recipe for disaster. Enterprise-class key management products can synchronize keys between multiple key managers. Remote storage tools should connect to the local key manager to avoid WAN dependency and latency. The biggest issue with this design is typically ensuring the different locations synchronize quickly enough, which tends to be more of an issue for distributed applications balanced across locations than for a hot standby sites, where data changes don't occur on both sides simultaneously. Another major concern is ensuring you can centrally manage the entire distributed deployment, rather than needing to log into each site separately.

Each of those meta-architectures can manage keys for all of the storage options we see in use, assuming the tools are compatible, even using different products. The encryption engine need not come from the same source as the key manager, so long as they are able to communicate.

That's the essential requirement: the key manager and encryption engines need to speak the same language, over a network connection with acceptable performance. This often dictates the physical and logical location of the key manager, and may even require additional key manager deployments within a single data center. But there is **never** a single key manager. You need more than one for availability, whether in a cluster or using a hot standby.

As we mentioned under best practices, some tools support distributing only needed keys to each 'local' key manager, which can strike a good balance between performance and security.

![Distributed Data Center Architecture](./traditional-distributed.png)

## Applications

There are as many different ways to encrypt an application as there are developers in the world (just ask them). But again we see most organizations coalescing around a few popular options:

* **Custom:** Developers program their own encryption (often using common encryption libraries), and design and implement their own key management. These are rarely standards-based, and can become problematic if you later need to add key rotation, auditing, or other security or compliance features.
* **Custom with external key management:** The encryption itself is, again, programmed in-house, but instead of handling key management itself, the application communicates with a central key manager, usually using an API. Architecturally the key manager needs to be relatively close to the application server to reduce latency, depending on the particulars of how the application is programmed. In this scenario, security depends strongly on how well the application is programmed.
* **Key manager software agent or SDK:** This is the same architecture, but the application uses a software agent or pre-configured SDK provided with the key manager. This is a great option because it generally avoids common errors in building encryption systems, and *should* speed up integration, with more features and easier management. Assuming everything works as advertised.
* **Key manager based encryption:** That's an awkward way of saying that instead of providing encryption keys to applications, each application provides unencrypted data to the key manager and gets encrypted data in return, and *vice-versa*.

We deliberately skipped file and database encryption, because they are variants of our "traditional data center storage" category, but we do see both integrated into different application architectures.

Based on our client work (in other words, a lot of anecdotes), application encryption seems to be the fastest growing option. It's also agnostic to your data center architecture, assuming the application has adequate access to the key manager. It doesn't really care whether the key manager is in the cloud, on-premise, or a hybrid.

## Hybrid Cloud

Speaking of hybrid cloud, after application encryption (usually in cloud deployments) this is where we see the most questions. There are two main use cases:

* **Extending existing key management to the cloud:** Many organizations already have a key manager they are happy with. As they move into the cloud they may either want to maintain consistency by using the same product, or need to support a migrating application without having to gut their key management to build something new. One approach is to always call back over the network to the on-premise key manager. This reduces architectural changes (and perhaps additional licensing), but often runs into latency and performance issues, even with a direct network connection. Alternatively you can deploy a virtual appliance version of your key manager as a 'bastion' host, and synchronize keys so assets in the cloud connect to the distributed virtual server for better performance.
* **Building a root of trust for cloud deployments:** Even if you are fully comfortable deploying your key manager in the cloud, you may still want an on-premise key manager to retain backups of keys or support interoperability across cloud providers.

Generally you will want to run a virtual version of your key manager within the cloud to satisfy performance requirements, even though you *could* route all requests back to your data center. It's still essential to synchronize keys, backups, and even logs back on-premise or to multiple, distributed cloud-based key managers, because no single instance or virtual machine can provide sufficient reliability.

![Hybrid Cloud Architecture](./hybrid-cloud.png)

## Bring Your Own Key

This is a very new option with some cloud providers who allow you to use an encryption service or product within their cloud, while you retain ownership of your keys. For example you might provide your own file encryption key to your cloud provider, who then uses it to encrypt your data, instead of using a key they manage.

The name of the game here is 'proprietary'. Each cloud provider offers different ways of supporting customer-managed keys. You nearly always need to meet stringent network and location requirements to host your key manager yourself, or you need to use your cloud provider's key management service, configured so you can manage your keys yourself.