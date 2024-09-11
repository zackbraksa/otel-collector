# Otel-collector

## Running the collector

Run the following command to start the collector and the other services

```bash
docker compose up -d
```

Inside your app code, update the endpoint to the collector `http://localhost:4318/v1/traces`

For example, in Ruby:

```ruby
OpenTelemetry::SDK.configure do |c|
    ... # other configurations
    c.add_span_processor(
      OpenTelemetry::SDK::Trace::Export::BatchSpanProcessor.new(
        OpenTelemetry::Exporter::OTLP::Exporter.new(endpoint: 'http://localhost:4318/v1/traces')
        )
    )
    ... # other configurations
end
```

## Viewing the traces

### Zipkin

- Open <http://localhost:9411/zipkin/> in your browser

### Jaeger

- Open <http://localhost:16686/> in your browser
