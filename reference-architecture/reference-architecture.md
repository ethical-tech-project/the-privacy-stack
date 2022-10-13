# Privacy Stack Reference Architecture v1


# Problem Statement

Empower technologists to architect, design, build and maintain systems that respect privacy by design and process data ethically. The right solution is the one that can be implemented once and withstand the changing regulatory compliance landscape. By clearly articulating the tradeoffs such solution supports both securing the data and extracting value from data. With the right set of controls in place every stakeholder can act independently to orchestrate an organization’s posture towards privacy compliance.



<p id="gdcalert1" ><span style="color: red; font-weight: bold">>>>>>  gd2md-html alert: inline image link here (to images/image1.png). Store image on your image server and adjust path/filename/extension if necessary. </span><br>(<a href="#">Back to top</a>)(<a href="#gdcalert2">Next alert</a>)<br><span style="color: red; font-weight: bold">>>>>> </span></p>


![alt_text](images/image1.png "image_tooltip")



# Gathering Requirements


## In Scope



1. **Purpose** - Make purpose a ‘first-class citizen’ in the consideration set for processing data through systems to **declare**, **enforce**, and **audit** permissions.
2. **Control** - Afford data owners the means to control their data through the **granting**, **revoking**, and **enforcing** of permissions and the ability to execute data **control operations**.
3. **Recognition** - Make explicit the **recognition** and identification of all entities participating in the data transaction with associated **registration**, **verification**, and **revocation** procedures.
4. **Transmission** - Support transmission of instructions and permissions from end to end across data supply chains through **subscription** and **broadcasting** procedures across the chain and **auditing** and **enforcement** procedures within each link.
5. **Rectification** - Take remedial steps to **rectify** instances when permissions or instructions are not respected and **monitor** and **alert** for such instances.
* What are permissions?
* What is purpose? 
* What’s the data supply chain?


```
Copied from the IG example, to support our pattern matching

```



* <code><em>Users should be able to upload photos and view the photos they have uploaded</em></code>
* <code><em>Users should be able to follow other users</em></code>
* <code><em>Users can view feeds containing posts from the users they follow</em></code>


## Out of Scope



* Design and implementation of the required identity systems
* Some topics concerning general security of the system, like the encryption protocols for data at rest or in transit.
* Trusted path
* Process-oriented strategies that ensure a deployment supports an organization’s legal policies and agreements.


```
From the IG example, for pattern matching

```



* <code><em>Sending and receiving messages from other users</em></code>
* <code><em>Generating ML based personalized rec's to discover new content and people</em></code>


# The Privacy Stack

_Describes the structure of this section of the document. The subsections on each archetype scenario are standalone, with the exception of more complicated archetypes that may require reading the Simple app + the more complex archetype scenario. Imagine the reader is interested in supply chain … the reader’s attention is on Simple + Supply Chain. _



* Components (?)
* The functions (e.g. post a picture to Instagram [Fig 2.](https://live.staticflickr.com/65535/51824416827_25bdf72ec6_h.jpg))
    * Constructing data catalog (metadata)
    * Obtaining permissions
    * Defining policies
    * Purpose limitation processing and access control
    * Respecting DSRs – delete, port etc.
    * Controller ⇔ Processor
    * Supply chain permissioning 
* The archetype scenarios:
    * Simple app - client, server, database
    * Advance app - adding 3rd party data integrations (orchestration)
    * Processor app - adding multi tenant
    * Supply chain - nth party chain of permissions


# Simple app


## Architecture

An example of the most basic application setup consisting of clients, mobile and desktop, and a back-end server and a database. Such applications support serving up pages and content, and may offer additional functionality such as personalization. Users of the app provide information to support a range of offerings, such as authentication and identity verification, payments and shipment when relevant, and preferences such as likes and dislikes. Data is collected explicitly, such as web forms, and/or implicitly, such as identifiers/cookies…



<p id="gdcalert2" ><span style="color: red; font-weight: bold">>>>>>  gd2md-html alert: inline image link here (to images/image2.png). Store image on your image server and adjust path/filename/extension if necessary. </span><br>(<a href="#">Back to top</a>)(<a href="#gdcalert3">Next alert</a>)<br><span style="color: red; font-weight: bold">>>>>> </span></p>


![alt_text](images/image2.png "image_tooltip")



## Privacy Stack System Components



<p id="gdcalert3" ><span style="color: red; font-weight: bold">>>>>>  gd2md-html alert: inline image link here (to images/image3.png). Store image on your image server and adjust path/filename/extension if necessary. </span><br>(<a href="#">Back to top</a>)(<a href="#gdcalert4">Next alert</a>)<br><span style="color: red; font-weight: bold">>>>>> </span></p>


![alt_text](images/image3.png "image_tooltip")



## Component Design (relevant functionality)

System components ->  privacy stack components 



* Constructing data catalog (metadata)



<p id="gdcalert4" ><span style="color: red; font-weight: bold">>>>>>  gd2md-html alert: inline image link here (to images/image4.png). Store image on your image server and adjust path/filename/extension if necessary. </span><br>(<a href="#">Back to top</a>)(<a href="#gdcalert5">Next alert</a>)<br><span style="color: red; font-weight: bold">>>>>> </span></p>


![alt_text](images/image4.png "image_tooltip")



## API Design

How do you ask for permissions? 

Consent API: obtain, modify, propagate

Within the API design we may have branches:



* User has one identity
* User may have more than one identity


# Advanced application


## Architecture


## Privacy Stack System Components


## Component Design (relevant functionality)

System components ->  privacy stack components 


## API Design


# Processor application


## Architecture


## Privacy Stack System Components


## Component Design (relevant functionality)

System components ->  privacy stack components 


## API Design


# Data Supply Chain Ecosystem


## Architecture


## Privacy Stack System Components


## Component Design (relevant functionality)

System components ->  privacy stack components 


## API Design


# Data models


## Permits


## Metadata


## Policies


# References

_How do we situate this work among related efforts?  Between now and EOY 2022, review and index. _



* Supplemental approach: as we seek feedback and input, ask people their thoughts and recommendations. 
1. Deprecated Privacy Stack Reference Architecture V1
2. 

 \
