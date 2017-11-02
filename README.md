# CQRS/ES best practices

Best practices, guidance, and anti-patterns to avoid when building an application following CQRS/ES principles.

## Guidance

### Define a schema for commands and events

> Services share schema and contract, not class.

Don't share types (i.e. .NET classes compiled into assemblies) as a way to express contracts in a messaging system.

Do define and share a schema and contract. Publish it for consumers to build their own internal representation of your data.

#### Examples

- [JSON Schema](http://json-schema.org/)
- [Protocol Buffers](https://developers.google.com/protocol-buffers/)

#### Further reading

- [At the Boundaries, Applications are Not Object-Oriented](http://blog.ploeh.dk/2011/05/31/AttheBoundaries,ApplicationsareNotObject-Oriented/) by Mark Seemann
- [Data/Contract Coupling in Messaging](https://channel9.msdn.com/Blogs/Subscribe/DataContract-Coupling-in-Messaging) by Clemens Vasters.

## Read model

### Autonomous read model projections

Don't share data between projections.

Do use autonomous projectors responsible for their own data. Projectors should run independently, allowing them to track their own progress and be rebuilt as required.

#### Further reading

- [The Ugly of Event Sourcing–Real-world Production Issues](http://www.continuousimprover.com/2017/11/the-ugly-of-event-sourcingreal-world.html)

### Projectors should never crash

Don't enforce consistency rules in your read model projection.

Do follow Postel's robustness principle:

> Be conservative in what you send, be liberal in what you accept.

## Versioning

#### Further reading

- [Versioning in an Event Sourced System](https://leanpub.com/esversioning)

## Data migration

#### Further reading

- [The Dark Side of Event Sourcing: Managing Data Conversion](http://files.movereem.nl/2017saner-eventsourcing.pdf)

---

## Contributing

Pull requests gladly accepted for your best practices, advice, and guidance.
