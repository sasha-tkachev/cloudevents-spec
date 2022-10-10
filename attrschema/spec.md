# CloudEvent Attributes Schema - Version 0.1-wip

## Abstract
Attrschema defines the media type `application/attrschema+json`, 
a JSON-based format for describing the structure of [CloudEvent 
context attributes][context-attributes]. 
Attrschema asserts what the CloudEvent attributes MUST look like, ways to extract 
information from them, and how to interact with them.

## Introduction
Attrschema is a JSON media type for defining the structure of CloudEvent context attributes. 
Attrschema is intended to define validation and documentation of CloudEvent attributes.

This specification defines Attrschema core terminology and mechanisms, 
including pointing to another Attrschema by reference.

## Conventions and Terminology 
The keywords "MUST", "MUST NOT", "REQUIRED", "SHALL", "SHALL NOT", "SHOULD",
"SHOULD NOT", "RECOMMENDED", "MAY", and "OPTIONAL" in this document are to be
interpreted as described in [RFC 2119](https://tools.ietf.org/html/rfc2119).

The terms "JSON", "JSON text", "JSON value", "member", "element", "object", 
"array", "number", "string", "boolean", "true", "false", and "null" in this 
document are to be interpreted as defined in RFC 8259 [RFC8259](https://tools.ietf.org/html/rfc8259).

## Overview 
This document proposes a new media type "application/attrschema+json" to identify a 
Attrschema for describing CloudEvent attributes. Attrschema is defined inside a JSON 
document, however it is intended to support many data formats that CloudEvent MAY be 
represented as.

Attrschema uses keywords to assert constraints on CloudEvent attribute or annotate 
those attributes with additional information.


## Definitions
### CloudEvent
Event [as defined in the CloudEvents specification](../cloudevents/spec.md#event)

### Type System
The type system of Attrschema is identical to [the type system defined in the 
CloudEvent Specification](../cloudevents/spec.md#type-system)

More specifically this type system defines the following types: 
- `Boolean` - a boolean value of "true" or "false".
- `Integer` - A whole number
- `String` - Sequence of allowable Unicode characters. 
- `Binary` - Sequence of bytes.
- `URI` - Absolute uniform resource identifier.
- `URI-reference` - Uniform resource identifier reference.
- `Timestamp` - Date and time expression using the Gregorian Calendar.

Attrschema validates attributes with values of the given types.

### Context Attributes
Context Attributes [as defined in the CloudEvents specification][context-attributes]

### Attrschema Document
An Attrschema document, or simply a schema, is a JSON document used to describe 
attributes of a CloudEvent.

A JSON Schema MUST be an object.

### Attrschema Objects and Keywords
Object properties that are applied to the instance are called keywords, 
or schema keywords. Broadly speaking, keywords fall into one of 2 categories:

- assertions:
  - produce a boolean result when applied to a CloudEvent
- annotations
  - attach information to an instance for application use
  
Keywords which are properties within the same schema object are referred to as adjacent keywords.

An Attrschema MAY contain properties which are not schema keywords. 
Unknown keywords SHOULD be treated as annotations, where the value of the keyword is 
the value of the annotation.

An empty schema is an Attrschema with no properties, or only unknown properties.

[context-attributes]: ../cloudevents/spec.md#context-attributes