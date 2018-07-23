---
published: true
---


# Introduction #

In recent years, the most fundamental transformation in IT landscape has been the emergence of cloud computing and it’s rapid and universal adoption by large, midsize and small enterprises operating across diverse industries. There has been a strategic shift from *‘build to consume’* and enterprises are taking huge strides in migrating a large number of their traditional and virtualized on-premises workloads onto a cloud computing infrastructure.

A comprehensive cloud infrastructure survey conducted by McKinsey predicts that enterprises’ adoption of Infrastructure as a Service (IaaS) as their primary environment for running application workloads will jump significantly from 10% in 2015 to 51% in 2018. 

The benefits of migrating to a cloud infrastructure are fairly obvious and compelling like lower CapEx, OpEx and maintenance costs, unlimited scalability on demand, redundancy,  24*7 availability,  best-in-class enterprise security, monitoring and compliance. However the business and technical risks associated with undertaking such migrations are often manifold and less well understood. 

In this blog post, i’ll briefly describe some commonly adopted strategies for migrating your application workloads on to any cloud infrastructure. Additionally, I’ll provide a checklist to analyze your application workloads for their suitability for migration and lay down some guidelines for on-boarding applications successfully on to a cloud environment.

----------
# Defining Cloud Migration Strategy #

In the process of strategizing their approach to cloud adoption, the first order of business for enterprises is often to dissipate the confusion surrounding the crowded landscape of different cloud architectures, service, deployment and hosting models, vendor platform, SLAs covering security, data governance, disaster recovery etc. Additionally, there is a laundry list of technical considerations like security, multi-tenancy, suitability of workloads for migration, evaluation of automated tools to handle migration and financial considerations that should be clearly addressed for a smooth transition onto the cloud.

I’ll address one of the key challenges in the mix which is to determine the path by which each application workload can potentially be transitioned on to the cloud. There are several paths to consider - although categorization provided by Gartner is one of the most widely accepted. The categories for cloud migration are described below -

***Lift and Shift***

This is the simplest migration strategy that involves moving the underlying infrastructure to run on virtual servers in the cloud and then porting the legacy applications to the new environment "as-is" without performing any refactoring. 

This low-barrier-to-entry approach can provide quick gains for enterprises who incur significant operational expenditure to run workloads in their current on-premise data centers. It causes minimal disruption to the applications that are being migrated. The transition process itself is significantly faster and much less costly requiring less resources.

However, this strategy has several limitations. Firstly, not all applications are suitable for lift and shift style migration especially if they are resource intensive or have any dependencies on any third party services that may need licenses to run in the cloud. Secondly, it comes up short in realizing the optimal and tangible benefits of a modern cloud platform in terms of enhanced scalability,  availability, performance, security etc. In fact, it may be more expensive to run certain workloads in the cloud without making any refactoring whatsoever. 

A lift and shift migration process typically entails the following steps as illustrated in the diagram below:

  
  ![an image alt text]({{ site.baseurl }}/images/post1_diag1.png "an image title")

Most cloud platform providers provide some tools to automate lift and shift tasks. Amazon AWS provides tools, most notably Snowball and VM Import/Export to migrate petabyte-scale data and virtual machines in and out of the public cloud.

***Refactoring***

This entails making major changes to your application code and/or configuration in order to migrate them over to the cloud. This typically follows a determination that your application, in its current state, is not suitable to be run on the cloud. In most cases your architectural design choices seems to pose severe limitations on your ability to scale out the application, recover gracefully from hardware failures, improve performance and build new features. Once refactoring is completed, applications should be able to run natively on a PaaS rather than having to be installed within custom VMs running on the cloud. This leads to a better level of integration between the applications inside the PaaS. It allows the customer to focus on applications rather than the platform. However, the migration effort is much more costlier, riskier and time consuming.

***Re-Platforming***

This migration strategy is ideal for customers who want to modernize their applications by extending them to the cloud and make them operate as part a larger distributed system. This involves taking advantage of horizontally scalable cloud services delivered by PaaS vendors like swapping your local RDBMS databases with datastore-as-service offering like RDS or switching your messaging systems with SNS service from AWS. 

Re-platformed apps benefits from dynamic allocation and reallocation of resources, autoscaling, availability and improved security. Additionally, it disrupts the traditional software licensing model and replace it with utility and subscription based pricing model that cloud vendors offer, resulting in lower overall costs of operation.

However, the cost of re-platforming apps is significant higher since it inevitably requires code changes to perform more natively on a cloud platform. Furthermore, it need building up sufficient technical expertise among your IT staff on various cloud platforms services.  

***Cloud Native Apps***

It is an approach where the application is fully compliant with the cloud computation model and adheres to the cloud first principles. It also means exclusively utilizing the cloud platform for application development, deployment and operation. Cloud native applications operate at the highest level of abstraction from the underlying IaaS or PaaS platform. They utilize the full capabilities of the platform which does all of the undifferentiated heavy lifting on their behalf like routing, load balancing, scaling, fault tolerance, user management, auditing etc. Converting legacy monolithic applications to cloud native is complex and in most situations involves a complete re-architecture of the existing system across the technology stack. Additionally, you need to cultivate a devOps culture within your organization that enables continuous integration, delivery and deployment of applications in a fully automated fashion.

There are four factors that are fundamental to building and delivering cloud native apps, as illustrated below.

![an image alt text]({{ site.baseurl }}/images/post1_diag2.png "an image title")

Composable architecture means decomposing a traditional monolith application into micro services and/or serverless components. This is the first step towards realizing the true promise of a cloud native architecture. A time-consuming task is to identify all external dependencies, isolate them and gradually remove them. You would need to create APIs as a front end to all the legacy services, then slowly start replacing various subcomponents of those systems that cannot be migrated to the cloud.

Another requirement is to utilize a Structured platform built expressly to run cloud native apps so that IT operations can focus on tasks that deliver most strategic impact to your organization rather than focus on undifferentiated tasks like deployment automation, gathering health metrics, providing application visibility, monitoring etc. Cloud Foundry PaaS from Pivotal is an excellent example of such a structured platform that takes the pain out of continuous delivery of cloud native apps.

It is also extremely important for process, cultural, and organizational changes to accompany the technical changes so as to deliver continuously in the cloud environment. Automation of the entire software delivery pipeline is not possible unless there is enhanced collaboration among all the teams with a shared responsibility. There needs to be a collective ownership over the entire development-to-operations life cycle of the software.


----------

# Analyzing Workloads for Migration #

A key decision that needs to be made along with determining your overarching cloud migration strategy is to analyze and select workloads that are suitable for migration. Most organizations have a heterogenous mix of new, legacy and third-party applications. Accordingly, each of these applications needs to evaluated and categorized in terms of their migration complexity, costs and risks. Each of them need to assigned a appropriate migration method that minimizes all of the above.

There are typically two broad considerations to make when deciding the cloud deployment model and hosting options -

Degree of control that a customer needs on the hardware, hypervisor, OS, middleware and software stack to run workloads on the cloud. Accordingly the deployment model could be IaaS, PaaS, SaaS or some combination thereof.

Security, data governance and compliance requirements for application data,. Accordingly, the model could be a private, public or hybrid cloud.

It is a complex process to navigate your application landscape and analyze the workloads that provides the best tradeoff between the ease of migration and potential cost benefits that accrue from the cloud. Asking the following questions could be the first step towards rationalizing your application portfolio and determining their business criticality.

 - Is your application data business-sensitive ? How is it secured ?

 - Are there any specific security and compliance requirements (e.g. encryption, isolation etc) ?

 - What supporting service requirements does the workload have to satisfy (eg, in terms of backup, disaster recovery, monitoring) ?

 - What are the performance requirements of the application like response rates, transaction rates, number of simultaneous users, volume of data usage, failure recovery SLAs, scalability,

 - What is the application architecture ? Is it a monolith or distributed app, what are the external dependencies and degree of coupling among the subsystems Can the application services be scale horizontally ?
    
 - What are the dependencies and integration touch points with other workloads ? What OS, databases and application servers are being

 - What are the CPU, memory, network and storage requirements and what will it cost to provide these in a cloud environment ?
    
 - How many hours/people are required to support the workload and what do they cost ? What are the costs of licensing and operational costs ? 
    
 - Does the cloud provider offer better disaster recovery capabilities than you currently use ?

As cloud platforms have matured over the years, there is a growing trend within organizations to architect and/or refactor applications to take full advantage of the platform. Greenfield applications provides an excellent opportunity to start building on a cloud platform using cloud-first principles from day one. However, legacy migration demands a more incremental approach where you can start transitioning business logic to the cloud by creating cloud-native microservices that will strangle legacy components, one at a time. To ensure a seamless integration between the new cloud workloads and services that are not migrated, it may be necessary to build a hybrid cloud infrastructure comprising of your on-premise data center and the public/private cloud.

There are some basic software architecture principles that are absolutely critical to ensure your application works well on any cloud provider platform and realizes all the benefits of performance, scalability and availability. Most of these principles derive from the fact that any cloud computing infrastructure is ephemeral, highly distributed and prone to intermittent failures. Most applications need some degree of refactoring to adhere to those principles and qualify as cloud ready. A quick look at these technical guidelines will help you determine which application workloads can be migrated with least amount of refactoring.

 - Processes within your application needs to be stateless and share

 - Processes within your application should be designed to be disposable
   at any time. They should start and stop quickly with absolutely
   minimal overhead.

 - Avoid in-memory sessions or stateful user context, move that to data
   stores.

 - All static content should be deployed to a cloud-based storage
   service that can deliver them directly to the client without wasting
   instance resources.

 - As a strategy, consider keeping dynamic data closer to the compute
   instances and static data closer to the end-user.

 - Applications should avoid writing anything to the local file system,
       including application event logs.
       
 - Avoid application clustering using shared disk architecture or using
       IP multicast protocols for cluster synchronization.
       
 - Externalize all application configuration into environment variables
       or use a special purpose external configuration server.

 - All application dependencies must be declared and isolated.
 
 - Any long running distributed transactions cannot be ported to the
       cloud environment. Applications need to embrace a eventually
       consistent model.

 - Applications should not rely on OS-specific features like OS-level
       schedulers  like cron.
       
 - Applications should try to decouple components and databases to the
       extent possible so that they can be scaled independently of each
       other.


------------

# On-Boarding Workloads #

Once the application workloads have been identified for migration, they must be prepared for on-boarding on to the cloud environment. Successful application on-boarding is all about careful planning and preparation. The steps involved in on-boarding are illustrated below.

![an image alt text]({{ site.baseurl }}/images/post1_diag3.png "an image title")

Preparing the application for migration involves implementing all the refactoring /re-platforming changes identified for it to work well in the cloud. Also, it usually involves containerization or virtualization of the workload, if not already done so. 

Once the application is ready, the next step is to provision the resources on the cloud environment based on the number or type of virtual machines required for the migration. Any additional storage, database, network, compute instances need to be provisioned.

This is typically followed by the actual transfer of the application and any associated databases and services which are being migrated along with the application. It also requires setting up environment metadata which is often very provider-specific. Account structures, users, permissions, policies, load balancers, and the like vary from cloud to cloud. Ensure data security controls are not compromised at any stage during the migration process.

For a smooth, seamless integration it is necessary to establish a 2-way network connectivity between your existing on-premise network and the target cloud environment. This helps in the migration process itself and allows for any integration or aggregation of capabilities across the network between your on-premise data center and the cloud.

The final steps are to test and validate the application deployment in the cloud and ensure all the technical testing (functional, integration, performance, security), user acceptance are passing without any failures. Special attention needs to given to check data consistencies especially after the databases are replicated and synchronized onto the cloud.

Once the cloud  deployed application is qualified, it is time to cutover and retire the old application instances. 

After the migration is accomplished successfully, it is necessary to monitor the application and its usage patterns while it is operating in the cloud. There are a variety of tools available that can help in providing application-level insights and monitoring.

# Conclusion #
----------
Migrating to a cloud is an extremely complex undertaking. It requires a comprehensive plan and a considerable level of organizational readiness to push through the cultural, technical and process changes needed to implement a *cloud first* strategy. A cohesive and consistent approach is needed to evaluate various service providers, cloud services, deployment models, data security requirements etc. The ultimate objective is to make informed decisions and strike a balance between operational risks and expected benefits.
