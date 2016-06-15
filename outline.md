# Linked Data Notifications

## Abstract



## Introduction

Linked Data Notifications is a specialised use of Linked Data Platform for sending and consuming notifications. It is not dependent on a complete implementation of LDP but designed to be compatible. This specification describes the particular features necessary to make it easy to exchange notifications in a decentralised, interoperable way.

This protocol assumes a modular approach to creating and storing data, in particular a decoupling between applications and data storage. Thus, where senders, receivers and consumers of notifications are independantly implemented and run on different technology stacks, this protocol allows them to seamlessly work together.

### Overview

A sender is triggered, either by a human or an automatic process, to deliver a notification to a server. The notification is data intended for the attention of the receiver, for example: a personal message from a friend; a pingback link; a comment on a blog post; an invitation to collaborate; a calendar reminder.

The sender discovers where to deliver the notification based on the addressee or subject of the notification - the receiver - who advertises the appropriate location on their server. The receiver also exposes the notification data (according to appropriate access control) for use by consumers.

Consumers discover the notifications in the same way as the sender, and my perform further processing on it, combine it with some other data, or simply present it in a suitable human-readable way.

### Summary

## Conformance

Implementations may be one or more of *senders*, *receivers* or *consumers*. For each feature, the specification indicates the role(s) for which the feature is normatively required.

## Protocol

### Discovery

### Sending

### Consuming

#### Authorisation

## Payload / content / Examples

## Extensibility

## Verification / integrity

## Security and privacy considerations


