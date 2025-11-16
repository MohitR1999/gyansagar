---
title: System Design
---
The key to build any system depends on how well it is planned for development. Hence, I decided to build the system 'on-paper' very well, before writing even a single line of code. I feel coding is the easiest part, getting the design right is the toughest one. 

In order to get the full grasp of this document, please go through the requirements first, which are listed [[Requirements|here]]
### Architecture Diagram
Below you can see the overall architecture diagram of the system that comprises of the client as well the server side components:
![[system-design.png]]
Essentially we'll have the following components:
- **ArthSaathi Mobile app**: This would be the product that the end users see and interact with. It has the responsibility to provide all the functionalities that we have mentioned in the Requirements specification.
- **API Gateway:** The one single point of communication between the server components and the outside world. All the requests will land here and will be routed to the concerned micro-service from here.
- **Auth Service:** This micro-service is responsible to authenticate the user and authorise the requests made by the user. All the logic related to managing user life-cycle will be placed here.
- **Money handler service:** This micro-service is responsible for managing all the expense and income related tasks, be it managing the categories of cash flow, recording the cash flow, modifying or updating the cash flow.
- **Reports service:** This micro-service is concerned with the generation of reports. I'm planning to extend the functionality to downloading the PDFs of the reports as well, so I believe putting that logic in a separate micro-service is justified.

It is worth noting that the *auth service* has its own database, whereas the *money handler* and the *reports service* operate on the common database that could only be manipulated by the money handler service.
