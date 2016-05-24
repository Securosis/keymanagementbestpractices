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
