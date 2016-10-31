*NOTE: This report template is a work in progress*

If you have an implementation in progress or plan to submit a report, add yours to this list for now until the tests and the report is finalised:

* Any [LDP implementation](https://www.w3.org/wiki/LDP_Implementations) (receiver)
* [node solid server](https://github.com/solid/node-solid-server) (receiver)
* [sloph](https://github.com/rhiaro/sloph) (receiver)
* [errol](https://github.com/linkeddata/errol) (sender)
* [dokieli](https://dokie.li/) (sender, consumer)
* [solid-inbox](https://github.com/solid/solid-inbox) (consumer)
* [solid-client](https://github.com/solid/solid-client) (sender)
* [solid-notifications](https://github.com/solid/solid-notifications)
  (sender, consumer)
* [solid words](https://github.com/melvincarvalho/vocab) (sender)
* [mayktso](https://github.com/csarven/mayktso) (receiver)
* [Virtuoso](https://github.com/openlink/virtuoso-opensource) + [ODS Briefcase](http://ods.openlinksw.com/wiki/ODS/OdsBriefcase) (receiver)
* [RDF::LinkedData::Notifications](https://github.com/kjetilk/p5-rdf-linkeddata-notifications) (very partial receiver)
* [IndieAnndroid](https://github.com/Kongaloosh/IndieAnndroid) which powers [kongaloosh](http://kongaloosh.com) (reciever)
* [pyldn](https://github.com/albertmeronyo/pyldn) (receiver)
* [Linked Edit Rules](https://github.com/albertmeronyo/linked-edit-rules) (sender)

---

# Linked Edit Rules

Implementation Home Page URL: https://github.com/albertmeronyo/linked-edit-rules

Source Code repo URL(s) (optional):
* [x] Open source implementation

Programming Language(s): Python

Developer(s): [Albert Meroño Peñuela](http://www.albertmeronyo.org)

Implementation Classes:

* [x] Sender
* [ ] Consumer
* [ ] Receiver

## Senders

### Discovery

* MUST be able to discover Inbox through a resource's `Link` header:
  * [ ] Relative URL in rel
  * [x] Absolute URL in rel
  * [ ] Multiple URLs in rel
  * ...
* MUST be able to discover Inbox through a resource's body:
  * [x] Test 1
  * [ ] Test 2
  * ...

### Sending

* MUST send a valid JSON-LD payload with `Content-Type: application/ld+json`
  * [ ] Test # So far sends text/turtle by default! Adding issue: https://github.com/albertmeronyo/linked-edit-rules/issues/1
  * ...
* MAY send a different valid RDF payload according to `Accept-Post` negotiation
  *  [ ] Test # TO DO: https://github.com/albertmeronyo/linked-edit-rules/issues/2
  *  ...
* [ ] MUST accept 201 as success # TO DO: https://github.com/albertmeronyo/linked-edit-rules/issues/3
* [ ] MUST accept 202 as success
* ...

### Security considerations
* [ ] This implementation can consume constraints (e.g., SHACL via `ldp:constrainedBy`) and assemble a compliant output to send. Please describe mechanism: _____


## Consumers

### Discovery

* MUST be able to discover Inbox through a resource's `Link` header:
  * [ ] Test 1
  * [ ] Test 2
  * ...
* MUST be able to discover Inbox through a resource's body:
  * [ ] Test 1
  * [ ] Test 2
  * ...

### Consuming

* MUST accept responses with JSON-LD content-type
  * [ ] Test
  * ...
* SHOULD include `Accept` header in request
  * [ ] Test
  * ...
* If no `Accept` header, SHOULD accept responses in JSON-LD or Turtle
  * [ ] Test
  * ...
* MUST find notification URIs through `http://www.w3.org/ns/ldp#contains`
  * [ ] Test
  * ...
* MAY find other information about the Inbox
  * [ ] Test
  * ...
* MAY fetch notifications from the Inbox, if doing so, MUST accept them in JSON-LD
  * [ ] Test
  * ...

What does this implementation do with retrieved notifications? _____

## Receivers

* MUST accept `POST` requests with `Content-Type: application/ld+json`
  * [ ] Test
  * ...
* Indicate the methods the `Accept-Post` header is announced in response to requests:
  * [ ] OPTIONS
  * [ ] HEAD
  * [ ] Other: ___
* [ ] MAY advertise other content types in `Accept-Post` header. Please list:
  * [ ] Turtle
  * [ ] HTML
  * [ ] Other: ___
* Indicate which type of response the receiver provides on a successful POST:
  * [ ] 201 Created
  * [ ] 202 Accepted

* MUST respond to `GET` requests with `Accept: application/ld+json` header with JSON-LD, and include `http://www.w3.org/ns/ldp#contains` listing:
  * [ ] Test
  * ...
* SHOULD return JSON-LD or Turtle if `Accept` header is missing:
  * [ ] JSON-LD
  * [ ] Turtle
* MAY respect other content-types in `Accept` header. Please list:
  * [ ] Turtle
  * [ ] HTML
  * [ ] Other: ___
* [ ] MUST respond with `415` for unavailable content types in Accept header.

### Security considerations

* [ ] This implementation has the capability to filter or verify incoming notifications (SHOULD). Please describe mechanism and criteria: _____
* [ ] This implementation restricts read access to notifications. Please describe mechanism and criteria: _____
* ...

### Storage

How does this implementation store notifications? (optional)

## Publishing

This is not a conformance class, but please indicate here documents or resources which advertise inboxes (whether these are your own implementation of a receiver, or someone else's).

Resource URL: http://www.linkededitrules.org

* [ ] Advertises Inbox using `Link` header
* [ ] Advertises Inbox using body
  * [ ] JSON-LD (MUST)
  * [ ] Turtle
  * [ ] HTML+RDFa
  * [ ] Other: ___
