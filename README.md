# CQRS/ES best practices

Best practices, guidance, and anti-patterns to avoid when building an application following CQRS/ES principles.

## Guidance

### Define a schema for commands and events

Don't share types (i.e. .NET classes compiled into assemblies) as a way to express contracts in a messaging system. 

Do define and share a schema. Publish it for consumers to build their own internal representation of the data.

#### Examples

- [JSON Schema](http://json-schema.org/)
- [Protocol Buffers](https://developers.google.com/protocol-buffers/)

#### Further reading

- [Data/Contract Coupling in Messaging](https://channel9.msdn.com/Blogs/Subscribe/DataContract-Coupling-in-Messaging) by Clemens Vasters.

## Contributing

Pull requests gladly accepted for your best practices, advice, and guidance.
