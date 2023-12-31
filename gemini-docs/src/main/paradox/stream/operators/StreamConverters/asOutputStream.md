# StreamConverters.asOutputStream

Create a source that materializes into an `OutputStream`.

@ref[Additional Sink and Source converters](../index.md#additional-sink-and-source-converters)

## Signature

@apidoc[StreamConverters.asOutputStream](StreamConverters$) { scala="#asOutputStream(writeTimeout:scala.concurrent.duration.FiniteDuration):akka.stream.scaladsl.Source[akka.util.ByteString,java.io.OutputStream]" java="#asOutputStream(java.time.Duration)" }

## Description

Create a source that materializes into an `OutputStream`. When bytes are written to the `OutputStream` they
are emitted from the source.

The `OutputStream` will no longer be writable when the `Source` has been canceled from its downstream, and
closing the `OutputStream` will complete the `Source`.

## Reactive Streams semantics

@@@div { .callout }
**emits** when bytes are written to the `OutputStream`

**completes** when the `OutputStream` is closed
@@@

## Example
Here is an example of a @apidoc[Source] that materializes into a @javadoc[java.io.OutputStream](java.io.OutputStream), and is connected to a Sink which concatenates the incoming @apidoc[akka.util.ByteString]s

Scala
:   @@snip [ToFromJavaIOStreams.scala](/gemini-docs/src/test/scala/docs/stream/operators/converters/ToFromJavaIOStreams.scala) { #asJavaOutputStream }

Java
:   @@snip [ToFromJavaIOStreams.java](/gemini-docs/src/test/java/jdocs/stream/operators/converters/ToFromJavaIOStreams.java) { #asJavaOutputStream }
