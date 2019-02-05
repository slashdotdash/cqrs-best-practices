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

### Value objects in domain events

Do use simple types in domain events (strings, numbers, lists).

Don't use value objects in events as events are immutable, whereas value objects may change over time.

### Use integration events between services, not domain events

Don't expose domain events outside of the service, or bounded context, that creates them.

Do use integration events.

An external integration event is a public event produced by a bounded context which may be interesting to other domains, applications or third party services. The purpose of integration events is to explicitly propagate committed transactions and updates to additional subsystems. You may convert and publish a domain event to external services, as an integration event, after it has been committed.

Using integration events makes it easier to change internal domain events, while allowing external integration events to provide a stable API to consumers. It also allows a service to only expose a subset of its domain events as integration events. Integration events can be enriched with additional data, such as from a read model projection, that is relevant to external uses.

#### Futher reading

- [Internal vs External Models](https://leanpub.com/esversioning/read#leanpub-auto-internal-vs-external-models)
- [Domain Events vs. Integration Events](https://medium.com/@arleypadua/domain-events-vs-integration-events-5eb29a34fdbc)
- [Domain events versus integration events](https://docs.microsoft.com/en-us/dotnet/standard/microservices-architecture/microservice-ddd-cqrs-patterns/domain-events-design-implementation#domain-events-versus-integration-events)

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
