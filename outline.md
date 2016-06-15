# Linked Data Notifications

## Abstract



## Introduction

Linked Data Notifications is a specialised use of Linked Data Platform for sending and consuming notifications. It is not dependent on a complete implementation of LDP but designed to be compatible. This specification describes the particular features necessary to make it easy to exchange notifications in a decentralised, interoperable way.

This protocol assumes a modular approach to creating and storing data, in particular a decoupling between applications and data storage. Thus, where senders, receivers and consumers of notifications are independently implemented and run on different technology stacks, this protocol allows them to seamlessly work together.

### Overview

A sender is triggered, either by a human or an automatic process, to deliver a notification to a server. The notification is data intended for the attention of the receiver, for example: a personal message from a friend; a pingback link; an comment on a blog post; an invitation to collaborate; a calendar reminder.

The sender discovers where to deliver the notification based on the addressee or subject of the notification - the receiver - which advertises the appropriate location to send it to. The receiver also exposes the notification data (according to appropriate access control) for use by consumers.

Consumers discover the notifications in the same way as the sender, and may perform further processing on it, combine it with some other data, or simply present it in a suitable human-readable way.

### Summary

## Conformance

Implementations may be one or more of *senders*, *receivers* or *consumers*. For each feature, the specification indicates the role(s) for which the feature is normatively required.

## Protocol

### Sending

### Receiving

Receivers MUST advertise an *Inbox* URL. In LDP terms, an Inbox may be either a `Container` or a `Resource`. Receivers must support *either* POST (for `Containers`) or PATCH (for `Resources`) at this URL (not both). 

If POST is supported, upon receipt of a POST request to this URL, the receiver MUST create a new resource containing the RDF data from the body of the POST request and MUST return either `HTTP 200 OK`, `HTTP 201 Created`, `HTTP 202 Accepted` or `HTTP 204 No Content`. In the case of a or 200 a `Content-Location` header pointing to the created resource MUST also be returned. In the case of a or 201 a `Location` header pointing to the created resource MUST also be returned. 

If PATCH is supported, upon receipt of a PATCH request to this URL, the receiver MUST update the resource at the URL to append the data in the body of the PAtCH request and MUST return either `HTTP 200 OK`, `HTTP 202 Accepted` or `HTTP 204 No Content`.

> TODO: Error for the ones not supported

### Consuming

#### Authorisation

## Payload / content / Examples

## Extensibility

## Verification / integrity

## Security and privacy considerations


