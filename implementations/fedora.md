
# Fedora Commons Repository

Implementation Home Page URL: https://wiki.duraspace.org/display/FF/Fedora+Repository+Home

Source Code repo URL(s) (optional): https://github.com/fcrepo4/fcrepo4
* [X] Open source implementation

Programming Language(s): Java

Developer(s): https://wiki.duraspace.org/display/FF/Fedora+Committers

Implementation Classes:

* [ ] Sender
* [ ] Consumer
* [X] Receiver

## Senders

### Discovery

* MUST be able to discover Inbox through a resource's `Link` header:
  * [ ] Relative URL in rel
  * [ ] Absolute URL in rel
  * [ ] Multiple URLs in rel
  * ...
* MUST be able to discover Inbox through a resource's body:
  * [ ] Test 1
  * [ ] Test 2
  * ...

### Sending

* MUST send a valid JSON-LD payload with `Content-Type: application/ld+json`
  * [ ] Test
  * ...
* MAY send a different valid RDF payload according to `Accept-Post` negotiation
  *  [ ] Test
  *  ...
* [ ] MUST accept 201 as success
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
  * [X] Test
  * ...
* Indicate the methods the `Accept-Post` header is announced in response to requests:
  * [X] OPTIONS
  * [X] HEAD
  * [X] Other: GET
* [X] MAY advertise other content types in `Accept-Post` header. Please list:
  * [X] Turtle
  * [ ] HTML
  * [X] Other: text/rdf+n3, text/n3, application/rdf+xml, application/n-triples, applicaton/sparql-update
* Indicate which type of response the receiver provides on a successful POST:
  * [X] 201 Created
  * [ ] 202 Accepted

* MUST respond to `GET` requests with `Accept: application/ld+json` header with JSON-LD, and include `http://www.w3.org/ns/ldp#contains` listing:
  * [X] Test
  * ...
* SHOULD return JSON-LD or Turtle if `Accept` header is missing:
  * [ ] JSON-LD
  * [X] Turtle
* MAY respect other content-types in `Accept` header. Please list:
  * [X] Turtle
  * [X] HTML
  * [X] Other: text/rdf+n3, text/n3, application/rdf+xml, application/n-triples
* [ ] MUST respond with `415` for unavailable content types in Accept header. _Fedora responds with `406` for unavailable content types_.

### Security considerations

* [X] This implementation has the capability to filter or verify incoming notifications (SHOULD). Please describe mechanism and criteria: Authorization is configurable, but many deployments use an implementation of WebAccessControl combined with servlet credentials. Using WebAC, authorization decisions are delegated to the applicable acl:Authorization triples, which can restrict access to certain resources (or resource hierarchy) based on user, group or the `rdf:type` of the parent resource.
* [X] This implementation restricts read access to notifications. Please describe mechanism and criteria: this is possible to configure using WebAccessControl in combination with servlet credentials. This would involve setting `<> acl:mode acl:Read` on the `acl:Authorization` resource that corresponds to the `ldp:inbox`.

### Storage

How does this implementation store notifications? (optional)

## Publishing

This is not a conformance class, but please indicate here documents or resources which advertise inboxes (whether these are your own implementation of a receiver, or someone else's).

Resource URL:

* [ ] Advertises Inbox using `Link` header
* [X] Advertises Inbox using body
  * [X] JSON-LD (MUST)
  * [X] Turtle
  * [X] HTML+RDFa
  * [X] Other: RDF/XML, N-Triples, N3
