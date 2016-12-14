*NOTE: This report template is a work in progress*

This file is a sample implementation report. Fork this repository, copy this file to a new `.md` file and change the name to your project name (in lower case with hyphens between words), and fill out the information in the report based on your implementation. When you are finished, submit a <a href="https://help.github.com/articles/using-pull-requests/">pull request</a> and your report will be reviewed and added to the main repository.

Complete this report by filling out the checkboxes as appropriate. To mark one as successful/complete/true, add an `x` between the brackets, e.g. `[x]`. If the statement does not apply to your implementation, use `[na]` and add a sentence explaining why it does not apply.

When you are complete, send a pull request with the addition of your report file. Please remove this entire top section, and any implementation class sections that do not apply to you, before submitting.


# dokieli

Implementation Home Page URL: https://dokie.li/

Source Code repo URL(s) (optional): https://github.com/linkeddata/dokieli
* [x] 100% open source implementation

Programming Language(s): HTML, JavaScript

Developer(s): [Sarven Capadisli](http://csarven.ca/)

Implementation Classes:

* [x] Sender
* [x] Consumer
* [ ] Receiver

## Senders

### Discovery

* MUST be able to discover Inbox through a resource's `Link` header:
  * [x] Test 1
  * [ ] Test 2
  * ...
* MUST be able to discover Inbox through a resource's body:
  * [x] Test 1
  * [ ] Test 2
  * ... 

### Sending

* MUST send a valid JSON-LD payload with `Content-Type: application/ld+json`
  * [x] Test
  * ...
* MAY send a different valid RDF payload according to `Accept-Post` negotiation
  * [x] Test
  *  ... 
* [x] MUST accept 201 as success
* [x] MUST accept 202 as success
* ...

### Security considerations
* [ ] This implementation can consume constraints (e.g., SHACL via `ldp:constrainedBy`) and assemble a compliant output to send. Please describe mechanism: _____

## Consumers

### Discovery

* MUST be able to discover Inbox through a resource's `Link` header:
  * [x] Test 1
  * [ ] Test 2
  * ...
* MUST be able to discover Inbox through a resource's body:
  * [x] Test 1
  * [ ] Test 2
  * ... 

### Consuming

* MUST accept responses with JSON-LD content-type
  * [x] Test
  * ...
* SHOULD include `Accept` header in request
  * [x] Test
  * ...
* If no `Accept` header, SHOULD accept responses in JSON-LD or Turtle
  * [na] Test
  * ...
* MUST find notification URIs through `http://www.w3.org/ns/ldp#contains`
  * [x] Test
  * ...
* MAY find other information about the Inbox
  * [x] Test
  * ...
* MAY fetch notifications from the Inbox, if doing so, MUST accept them in JSON-LD
  * [x] Test
  * ...

What does this implementation do with retrieved notifications? Optionally fetches more information by FYN exploration, assembles an output in HTML+RDFa, then inserts the result in applicable locations in the browser DOM (for HTML+RDFa).

## Receivers

* MUST accept `POST` requests with `Content-Type: application/ld+json`
  * [ ] Test
  * ...
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

Resource URL: 

* [ ] Advertises Inbox using `Link` header
* [x] Advertises Inbox using body
  * [ ] JSON-LD (MUST)
  * [ ] Turtle
  * [x] HTML/RDFa
  * [ ] Other: ___