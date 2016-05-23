Title: Evolving Encryption Key Management Best Practices for the Data Center

# Data centers and applications are changing, so is key management.

Cloud. DevOps. Microservices. Containers. Big Data. NoSQL.

We are in the midst of an IT transformation wave that's quite likely the most disruptive since we built the first data centers. One that's even more disruptive since the first days of the Internet due to the convergence of multiple vectors of change. From the architectural disruptions of the cloud, to the underlying process changes of DevOps, to evolving storage practices of Big Data and NoSQL databases. 

All of these significantly impact one of our most foundational data security controls — encryption. While encryption algorithms continue their steady evolution, encryption system *architectures* are forced to change at a much higher rate due to the rapid changes in the underlying infrastructure and applications themselves. And security teams face the challenge of supporting all these new technologies and architectures while still maintaining and protecting all the existing systems.

Within the practice of data at rest encryption, key management is often the center of this change. Keys must be managed and distributed in ever more complex scenarios, at the same time there is also increasing demand for encryption throughout our data centers (including cloud) and our application stacks.

This research highlights the emerging best practices for managing encryption keys for protecting data at rest  in the face of these new challenges. It also presents updated use cases and architectures for those areas where we see the most implementation questions. It's completely focused on data at rest, including application data; transport encryption is an entirely different issue, as is protecting data on employee computers and devices.

## How technology evolution affects key management

Technology is always changing, but there is reasonable consensus that the changes we are experiencing now are at a higher rate than even the early days of the Internet. For the most part, this is because we see a mix of both architectural and process changes within our data centers and applications. Cloud, increased segregation, containers, and micro services all change architectures, while DevOps and other emerging development and operations practices, alter development and management practices. Better (or worst, depending on your perspective) yet, all these changes mix and reinforce each other.

Okay, enough generalities, here are the top trends we see impacting data at rest encryption:

* **Cloud Computing:** Cloud is the single most disruptive force affecting encryption today. In fact, it's driving very large increases in encryption usage as organizations move into shared infrastructure. In some cases, this also drives increased use of encryption internally due to increased awareness, use of hybrid cloud, or in preparation for moving the data into the cloud. 

	Cloud doesn't merely affect adoption of encryption, it also fundamentally changes architectures. You can't simply move applications to the cloud without re-architecting them for the cloud (without seriously breaking things, trust us, we see it every day). This is especially true of encryption systems and key management, where integration, performance, and compliance all intersect to affect practices.
* **Increased Segmentation:** We have long moved past the days where flat architectures for data centers were acceptable. Cloud is massively segregated by default, and existing data centers increasingly add internal barriers. This affects key management architectures that now need to support different distribution models without adding management complexity.
* **Microservice architectures:** Application architectures themselves are also becoming more compartmentalized and distributed as we move away from monolithic designs into increasingly distributed, and sometimes ephemeral, services. This, again, increases the demands to distribute and manage keys at a wider scale without compromising security.
* **Big Data and NoSQL:** Big data isn't just a catch phrase, it encompasses a variety of new data storage and processing technologies. NoSQL isn't necessarily big data, but also alters data storage and processing. For example, we are now moving massive amounts of data outside of relational databases and into distributed, file system based repositories. This further challenges key management since we need to support distributed data storage and processing on larger data repositories than ever before.
* **Containers:** Containers continue the trend of distributing processing and storage (notice a theme?), yet do so on an even more-ephemeral basis where containers might appear in microseconds and disappear in minutes in response to application and infrastructure demands.
* **DevOps:** To best leverage this new changes and increase effectiveness and resiliency, DevOps continues to emerge as a dominant development and operational framework (not that there is any single definition of DevOps). It's a philosophy and collection of practices that tends to support extremely high rates of change and automation. This means it's essential key management practices integrate, or teams will simply move forward without support.

These technologies and practices aren't mutually exclusive. It is extremely common today to build a microservices based application inside containers running in a cloud provider that leverages both NoSQL and Big Data, all managed using DevOps. Encryption may need to support the individual application services, containers, virtual machines, and underlying storage, which might trace back to an existing enterprise data center via a hybrid cloud connection. 

It isn't always this complex, but sometimes it is, and key management practices are changing to keep pace and provide the right key, at the right time, to the right location, without compromising security, while still supporting all the traditional technologies. 