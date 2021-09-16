---
title: Light Speed Protocol
publisher: dhh1128
license: MIT
piuri: https://didcomm.org/light-speed-protocol/0.9
status: Production
summary: In one or two sentences, explain what problem this protocol solve, how it works, and other key characteristics.
tags:
  - faster-than-light-travel
  - star-wars
authors:
  - name: Your name
    email: you@github-email
  - name: Author without email

---

## Roles

> See [this note](https://github.com/hyperledger/aries-rfcs/tree/master/concepts/0003-protocols/roles-participants-etc.md) for definitions of the terms "role", "participant", and "party".

Provides a `formal name` (using backticks in markdown) for each role in the protocol, says who and how many can play each role, and describes constraints associated with those roles (e.g., "You can only issue a credential if you have a DID on the public ledger"). The issue of qualification for roles can also be explored (e.g., "The holder of the credential must be known to the issuer").

The formal names for each role are important because they are used when [agents discover one another's capabilities](https://github.com/hyperledger/aries-rfcs/tree/master/features/0031-discover-features). An agent doesn't just claim that it supports a protocol; it makes a claim about which *roles* in the protocol it supports. An agent that supports credential issuance and an agent that supports credential holding may have very different features, but they both use the _credential-issuance_ protocol. By convention, role names use lower-kebab-case and are compared case-sensitively.

## Connectivity

Describe any assumptions about simplex vs. duplex, which parties need to talk to which parties, etc.

## States

This section lists the possible states that exist for each role. It also enumerates the events (often but not always messages) that can occur, including errors, and what should happen to state as a result. A formal representation of this information is provided in a _state machine matrix_. It lists events as columns, and states as rows; a cell answers the question, "If I am in state X (=row), and event Y (=column) occurs, what happens to my state?" The [Tic Tac Toe example](https://github.com/hyperledger/aries-rfcs/blob/master/concepts/0003-protocols/tictactoe/README.md#states) is typical.

[Choreography Diagrams](
https://www.visual-paradigm.com/guide/bpmn/bpmn-orchestration-vs-choreography-vs-collaboration/#bpmn-choreography) from [BPMN](http://www.bpmn.org/) are good artifacts here, as are [PUML sequence diagrams](
http://plantuml.com/sequence-diagram) and [UML-style state machine diagrams](http://agilemodeling.com/artifacts/stateMachineDiagram.htm). The matrix form is nice because it forces an exhaustive analysis of every possible event. The diagram styles are often simpler to create and consume, and the PUML and BPMN forms have the virtue that they can support line-by-line diffs when checked in with source code. However, they don't offer an easy way to see if all possible flows have been considered; what they may NOT describe isn't obvious. This--and the freedom from fancy tools--is why the matrix form is used in many early RFCs. We leave it up to the community to settle on whether it wants to strongly recommend specific diagram types.

The formal names for each state are important, as they are used in [`ack`s](https://github.com/hyperledger/aries-rfcs/tree/master/features/0015-acks) and [`problem-report`s](https://github.com/hyperledger/aries-rfcs/tree/master/features/0035-report-problem)). For example, a `problem-report` message declares which state the sender arrived at because of the problem. This helps other participants to react to errors with confidence. Formal state names are also used in the agent test suite, in log messages, and so forth.

By convention, state names use lower-kebab-case. They are compared case-sensitively.

State management in protocols is a deep topic. For more information, please see [State Details and State Machines](https://github.com/hyperledger/aries-rfcs/blob/master/concepts/0003-protocols/state-details.md).

## Basic Walkthrough

Explain what happens from beginning to end. in a simple instance of the protocol. The goal is not to describe all the possibilities, but to show a typical ("happy-path") case so people get the main idea. Provide examples of the messages and explain their fundamental meaning and usage. All possible fields may not appear; an exhaustive catalog is saved for [Message Reference](#message-reference).

## Design By Contract

What preconditions must be met? What invariants apply? What postconditions are guaranteed under which circumstances? What side effects can occur? What can go wrong, when -- and how do errors affect the state of each party? Consider timeouts, malformed messages, mis-sequenced messages, etc. See [Design By Contract](https://en.wikipedia.org/wiki/Design_by_contract).

Error Code | Notes
--- | ---
out-of-memory | Possible in state `waiting-for-commit` when RAM is tight. Causes protocol to be abandoned by all parties.

## Security

What abuse could occur with malicious participants, eavesdroppers, denial-of-service, etc? What should be true about the [message trust contexts](https://github.com/hyperledger/aries-rfcs/blob/master/concepts/0029-message-trust-contexts/README.md)? What should be [repudiable or non-repudiable](https://github.com/hyperledger/aries-rfcs/blob/master/concepts/0049-repudiation/README.md)? What mechanisms does the protocol offer to cope with such issues?

## Composition

Supported Goal Code | Notes
--- | ---
aries.pay.cash | A goal code used by the Hyperledger Aries ecosystem. See RFC X.
dif.pay-direct | Approximately the same meaning in DIF ecosystems.

Can this protocol be used as a co-protocol? If yes, please include a coprotocol definition like the one shown [here](https://github.com/hyperledger/aries-rfcs/blob/master/concepts/0478-coprotocols/README.md#example).

## Message Reference

Unless the "Messages" section under "Basic Walkthrough" covered everything that needs to be known about all message fields, this is where the data type, validation rules, and semantics of each field in each message type are detailed. Enumerating possible values, or providing ABNF or regexes is encouraged. Following conventions such as [those for date- and time-related fields](https://github.com/hyperledger/aries-rfcs/tree/master/concepts/0074-didcomm-best-practices#date-time-conventions) can save a lot of time here.

Each message type should be associated with one or more roles in the protocol. That is, it should be clear which roles can send and receive which message types.

## Advanced Walkthroughs

This section is optional. It can be used to show alternate flows through
the protocol.

## Collateral

This section is optional. It could be used to reference files, code,
relevant standards, oracles, test suites, or other artifacts that would
be useful to an implementer. In general, collateral should be checked in
with the RFC.

## L10n

If communication in the protocol involves humans, then localization of
message content may be relevant. Default settings for localization of
all messages in the protocol can be specified in an `l10n.json` file
described here and checked in with the RFC. See ["Decorators at Message
Type Scope"](https://github.com/hyperledger/aries-rfcs/tree/master/concepts/0011-decorators#decorator-scope)
in the [Localization RFC](https://github.com/hyperledger/aries-rfcs/tree/master/features/0043-l10n).

## Implementations

## Endnotes

#### 1
Cite someone.

#### 2
Add an explanatory comment that wasn't worth including inline.
