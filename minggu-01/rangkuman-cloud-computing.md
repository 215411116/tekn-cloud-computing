# Teknologi cloud minggu 1
## Cloud computing

Cloud computing is the on-demand availability of computer system resources, especially data storage (cloud storage) and computing power, without direct active management by the user. Large clouds often have functions distributed over multiple locations, each location being a data center. Cloud computing relies on sharing of resources to achieve coherence and typically using a "pay-as-you-go" model which can help in reducing capital expenses but may also lead to unexpected operating expenses for unaware users.

## Value proposition
Advocates of public and hybrid clouds claim that cloud computing allows companies to avoid or minimize up-front IT infrastructure costs. Proponents also claim that cloud computing allows enterprises to get their applications up and running faster, with improved manageability and less maintenance, and that it enables IT teams to more rapidly adjust resources to meet fluctuating and unpredictable demand, providing burst computing capability: high computing power at certain periods of peak demand.

## Market
According to IDC, the global spending on cloud computing services has reached $706 billion and expected to reach $1.3 trillion by 2025. While Gartner estimated that the global public cloud services end-user spending forecast to reach $600 billion by 2023.[9] As per McKinsey & Company report, cloud cost-optimization levers and value-oriented business use cases foresees more than $1 trillion in run-rate EBITDA across Fortune 500 companies as up for grabs in 2030. In 2022, more than $1.3 trillion in enterprise IT spending is at stake from the shift to cloud, growing to almost $1.8 trillion in 2025, according to Gartner.

## History
The term cloud was used to refer to platforms for distributed computing as early as 1993, when Apple spin-off General Magic and AT&T used it in describing their (paired) Telescript and Personal Link technologies.In Wired's April 1994 feature "Bill and Andy's Excellent Adventure II", Andy Hertzfeld commented on Telescript, General Magic's distributed programming language:

> "The beauty of Telescript ... is that now, instead of just having a device to program, we now have the entire Cloud out there, where a single program can go and travel to many different sources of information and create a sort of a virtual service. No one had conceived that before. The example Jim White [the designer of Telescript, X.400 and ASN.1] uses now is a date-arranging service where a software agent goes to the flower store and orders flowers and then goes to the ticket shop and gets the tickets for the show, and everything is communicated to both parties."

- Early history
During the 1960s, the initial concepts of time-sharing became popularized via RJE (Remote Job Entry);[14] this terminology was mostly associated with large vendors such as IBM and DEC. Full-time-sharing solutions were available by the early 1970s on such platforms as Multics (on GE hardware), Cambridge CTSS, and the earliest UNIX ports (on DEC hardware). Yet, the "data center" model where users submitted jobs to operators to run on IBM's mainframes was overwhelmingly predominant.

    > "The beauty of Telescript," says Andy, "is that now, instead of just having a device to program, we now have the entire Cloud out there, where a single program can go and travel to many different sources of information and create a sort of a virtual service."

    The use of the cloud metaphor is credited to General Magic communications employee David Hoffman, based on long-standing use in networking and telecom. In addition to use by General Magic itself, it was also used in promoting AT&T's associated PersonaLink Services."

- 2000s
In July 2002, Amazon created subsidiary Amazon Web Services, with the goal to "enable developers to build innovative and entrepreneurial applications on their own." In March 2006 Amazon introduced its Simple Storage Service (S3), followed by Elastic Compute Cloud (EC2) in August of the same year. These products pioneered the usage of server virtualization to deliver IaaS at a cheaper and on-demand pricing basis.
    
    In early 2008, NASA's Nebula, enhanced in the RESERVOIR European Commission-funded project, became the first open-source software for deploying private and hybrid clouds, and for the federation of clouds.

    By mid-2008, Gartner saw an opportunity for cloud computing "to shape the relationship among consumers of IT services, those who use IT services and those who sell them"[25] and observed that "organizations are switching from company-owned hardware and software assets to per-use service-based models" so that the "projected shift to computing ... will result in dramatic growth in IT products in some areas and significant reductions in other areas."

    In 2009, the government of France announced Project Andromède to create a "sovereign cloud" or national cloud computing, with the government to spend €285 million. The initiative failed badly and Cloudwatt was shut down on 1 February 2020.
    
- 2010s
In February 2010, Microsoft released Microsoft Azure, which was announced in October 2008.
In July 2010, Rackspace Hosting and NASA jointly launched an open-source cloud-software initiative known as OpenStack. The OpenStack project intended to help organizations offering cloud-computing services running on standard hardware. The early code came from NASA's Nebula platform as well as from Rackspace's Cloud Files platform. As an open-source offering and along with other open-source solutions such as CloudStack, Ganeti, and OpenNebula, it has attracted attention by several key communities. Several studies aim at comparing these open source offerings based on a set of criteria.

    On March 1, 2011, IBM announced the IBM SmartCloud framework to support Smarter Planet.[40] Among the various components of the Smarter Computing foundation, cloud computing is a critical part. On June 7, 2012, Oracle announced the Oracle Cloud. This cloud offering is poised to be the first to provide users with access to an integrated set of IT solutions, including the Applications (SaaS), Platform (PaaS), and Infrastructure (IaaS) layers.
    
    In May 2012, Google Compute Engine was released in preview, before being rolled out into General Availability in December 2013.
    
    In 2019, Linux was the most common OS used on Microsoft Azure. In December 2019, Amazon announced AWS Outposts, which is a fully managed service that extends AWS infrastructure, AWS services, APIs, and tools to virtually any customer datacenter, co-location space, or on-premises facility for a truly consistent hybrid experience.
    
## Service models
Though service-oriented architecture advocates "Everything as a service" (with the acronyms EaaS or XaaS,[70] or simply aas), cloud-computing providers offer their "services" according to different models, of which the three standard models per NIST are Infrastructure as a Service (IaaS), Platform as a Service (PaaS), and Software as a Service (SaaS).[69] These models offer increasing abstraction; they are thus often portrayed as layers in a stack: infrastructure-, platform- and software-as-a-service, but these need not be related. For example, one can provide SaaS implemented on physical machines (bare metal), without using underlying PaaS or IaaS layers, and conversely one can run a program on IaaS and access it directly, without wrapping it as SaaS.

- Infrastructure as a service (IaaS)
Infrastructure as a service" (IaaS) refers to online services that provide high-level APIs used to abstract various low-level details of underlying network infrastructure like physical computing resources, location, data partitioning, scaling, security, backup, etc. A hypervisor runs the virtual machines as guests. Pools of hypervisors within the cloud operational system can support large numbers of virtual machines and the ability to scale services up and down according to customers' varying requirements. Linux containers run in isolated partitions of a single Linux kernel running directly on the physical hardware. Linux cgroups and namespaces are the underlying Linux kernel technologies used to isolate, secure and manage the containers. Containerisation offers higher performance than virtualization because there is no hypervisor overhead. IaaS clouds often offer additional resources such as a virtual-machine disk-image library, raw block storage, file or object storage, firewalls, load balancers, IP addresses, virtual local area networks (VLANs), and software bundles.[71]

- Platform as a service (PaaS)
PaaS vendors offer a development environment to application developers. The provider typically develops toolkit and standards for development and channels for distribution and payment. In the PaaS models, cloud providers deliver a computing platform, typically including an operating system, programming-language execution environment, database, and the web server. Application developers develop and run their software on a cloud platform instead of directly buying and managing the underlying hardware and software layers. With some PaaS, the underlying computer and storage resources scale automatically to match application demand so that the cloud user does not have to allocate resources manually.

- Software as a service (SaaS)
In the software as a service (SaaS) model, users gain access to application software and databases. Cloud providers manage the infrastructure and platforms that run the applications. SaaS is sometimes referred to as "on-demand software" and is usually priced on a pay-per-use basis or using a subscription fee.[77] In the SaaS model, cloud providers install and operate application software in the cloud and cloud users access the software from cloud clients. Cloud users do not manage the cloud infrastructure and platform where the application runs. This eliminates the need to install and run the application on the cloud user's own computers, which simplifies maintenance and support. Cloud applications differ from other applications in their scalability—which can be achieved by cloning tasks onto multiple virtual machines at run-time to meet changing work demand.[78] Load balancers distribute the work over the set of virtual machines. This process is transparent to the cloud user, who sees only a single access-point. To accommodate a large number of cloud users, cloud applications can be multitenant, meaning that any machine may serve more than one cloud-user organization.

- Mobile "backend" as a service (MBaaS)
In the mobile "backend" as a service (m) model, also known as backend as a service (BaaS), web app and mobile app developers are provided with a way to link their applications to cloud storage and cloud computing services with application programming interfaces (APIs) exposed to their applications and custom software development kits (SDKs). Services include user management, push notifications, integration with social networking services and more. This is a relatively recent model in cloud computing,[83] with most BaaS startups dating from 2011 or later but trends indicate that these services are gaining significant mainstream traction with enterprise consumers

- Serverless computing or Function-as-a-Service (FaaS)
Serverless computing is a cloud computing code execution model in which the cloud provider fully manages starting and stopping virtual machines as necessary to serve requests, and requests are billed by an abstract measure of the resources required to satisfy the request, rather than per virtual machine, per hour. Despite the name, it does not actually involve running code without servers. Serverless computing is so named because the business or person that owns the system does not have to purchase, rent or provide servers or virtual machines for the back-end code to run on.


