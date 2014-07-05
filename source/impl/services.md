title:  
date:  
categories: impl
---
<a name="SOA"> </a>
<a name="soa"> </a>

## <span class="sectioncount">2.9<a name="2.9"> </a></span> Using Resources with Services

Though FHIR Resources are primarily designed with for the [RESTful HTTP-based implementation](http.html),
it is not necessary to use a RESTful interface when exchanging the resources; one way that they can be exchanged 
is in the context of services. Service Oriented Architecture (SOA) is an architecture pattern using services to encapsulate and provide discreet pieces of application functionality to each other. Services communicate 
by invoking public interfaces and exchanging information (as parameters and outputs) in accordance to a 
well-defined service contract. 

FHIR resources or [bundles](extras.html#bundle) may be used as the parameters or outputs of service interfaces.

Generally, the definition of particular services is a domain or context specific task, and it is anticipated
that this would be done as separate specifications that make use of the underlying facilities defined
in this specification. Services defined like this are able to build on the common underlying platform
features defined in this specification such as REST or messaging, and add specific interactions where
appropriate. Alternatively, the service interfaces can build an entirely separate implementation. 
At this time, FHIR does not define any specific service interfaces as part of the specification, 
though alignment with service interface definitions provided by the 
[HL7 SOA work group](http://hssp.wikispaces.com/) will be considered if 
there is sufficient interest in this.

> **DSTU Notice**: The RESTful interface is a profile on the existing [HL7/OMG HSSP 
> RLUS specification](http://hssp-rlus.wikispaces.com/RLUS_FAQ) (see [comments on the RESTful specification](http.html#hdata)). 
> If there is interest, HL7 could define a SOAP equivalent to this. The main interest
> in this would be to provide a common technical base for other SOAP based services.

When implementing exchange of resources using a service-based approach, there are two 
aspects to keep in mind:

*   Technical requirements when exchanging resources
*   FHIR architectural issues to consider when using services

Both these impact on how services should manage exchanging resources in their design
and implementation.

<a name="tech"> </a>

## <span class="sectioncount">2.9<a name="2.9"> </a></span> Technical Requirements

Resources are designed so the package that is &quot;the resource&quot; consists of data (the content inside the resource,
and metadata - additional fields that are actually stored and exchanged outside the resource). In the 
RESTful context, these fields are part of the HTTP header, and their functionality is integrated into  
the HTTP exchange. When the resources are used with a service, this data must either be exchanged with
the resource, or the functionality they provide replaced in some way.

A key question in this regard is whether the resources that are exchanged across a service interface 
need to also be handled in a RESTful context around the service. For example, a decision support
provider service might receive a collection of resources on which a decision is required, and 
use an internal RESTful service to store and access them. In this case, it would need to take
the resources out of the service context, and use them in a RESTful context, and generally the
service would expect to see duplicate resources over time, where versions must be managed 
correctly. If the resources to be exchanged over services are also to
be exchanged with REST, the metadata will be required.

**Resource Identity**

All resources have a single identity (the full URL), and a logical id which may be maintained
as the resource moves from server to server (see [&quot;Managing Resource Identity&quot;](managing.html) for further 
discussion). Since this identity is used by any reference to the resource, it must be exchanged 
with the resource so that references from other resources to the one being exchanged can 
still be resolved.

Related to this, resources are modular units that refer to each other. Although 
resources stand-alone and are each processed independently, it's rarely possible 
to use a resource to achieve some clinical or business goal without retrieving the 
other referenced resources. Any use of resources in a service environment needs to 
address how these references can be resolved. This can be achieved by delegating 
the reference resolution to a RESTful framework, by ensuring that all the relevant 
resources are contained in the service call, or by making some service based arrangement
by which additional resources can be retrieved.

Services that exchange resources SHALL maintain resource identity.

**Resource Version**

Resources have two metadata elements relating to versioning: &quot;Version Id&quot; and &quot;Last Modified Date&quot;.
Because of data/time resolution issues, systems implementing concurrency solutions are 
strongly recommended to depend on the version id; the Last Modified Date is provided to
inform human users about information currency. 

Services typically assume that the information in the service calls is the latest 
information. As a consequence, explicit version tracking is often not part of a 
service call. However if the resources in the service call then need to be used
in a RESTful fashion, explicitly tracking the version and last modified date 
will make this subsequent usage much more efficient.

Services that exchange resources SHOULD include version information when the resources are exchanged.

**Capability Statement**

When using [RESTful exchange](http.html), [messaging](messaging.html), and [document based](documents.html) 
exchange, the [conformance statement](conformance.html) allows authoring and reading 
applications to describe how they use a resource. The conformance statement supports trading partner
negotiation from specification time through to run-time discovery. The conformance statement doesn't
provide any equivalent way to make declarations about services, though this might be added in 
the future if common requirements emerge. Services are expected to make appropriate arrangements
around discovery and compatibility, though it is expected that these will vary considerably. 

Services that exchange resources MAY choose to provide support for describing and 
changing descriptions of service implementations.

<a name="architecture"> </a>

## <span class="sectioncount">2.9<a name="2.9"> </a></span> Architectural Considerations

FHIR Resources are designed to make use in a wide variety of contexts. In particular,
FHIR resources are required to be suitable for use in a REST environment. This means
that there are number of design requirements and choices that impact on how suitable
resources are for use with services. 

If service use was the only consideration, different decisions would be made, and 
resources would be more suitable for use with services. However this would curtail
their usefulness and reusability in other contexts. 

**Resource References**

The most obvious impact is that resources [refer to each other using full URL
based references](references.html), and there are a number of rules around how these references are 
resolved. In the context of a service, this means that the references between modules 
carry this extra weight of choice and obligation, even when it might not be necessary.

**Explicit State**

All resources represent the various states of the record and real world entities involved
in a transaction explicitly. This is necessary for use in RESTful and document contexts,
where there is no explicit transaction. Service interactions are typically associated with
implicit semantics - a request to change the status of a particular resource to something
else, for example. The fact that resources carry this state explicitly as well as the 
transaction fixing state implicitly creates duplication between the two, and this will
need to be managed.

**Modularity**

The modularity of resources - which resources are defined, and why - is driven by 
a wide set of considerations around how they are used. Resources are a platform on 
which a set of business/clinical services of various kinds are provided. Accordingly, the resources
are defined for general use, and they can be expected to be less suitable for a 
particular service than custom defined structures. The pay back is wider re-use 
of the information that the service deals with.

 