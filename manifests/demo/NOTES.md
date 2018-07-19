# Demo Notes

## Istio Components

The Istio Service Mesh provides the following functionalities:

1. Routing. For example 90% of the traffic goes to the version 1 of a microservice
2. Support for microservices development, deployment and testing:
    - Timeouts, retries, balancing, fault-injection
3. Reporting: Logging, Distributed Tracing, Telemetry
4. Policy enforcement
5. Secure communication between micro services and strong identity.


Pilot is responsible for the items 1 and 2. Mixer is responsible for the items 3 and 4. Citadel is responsible for the item 5.

Envoy, the sidecar proxy, gets its routing and configuration tables from Pilot to implement the items 1 and 2. Envoy reports to Mixer about each request, to implement the item 3. Envoy asks Mixer to allow or forbid requests, to implement the item 4. Envoy gets certificates from CA to implement the item 5.

## OpenTracing

http://opentracing.io/documentation/

https://medium. com/opentracing/distributed-tracing-in-10-minutes-51b378ee40f1

http://kamon.io/documentation/1.x/core/basics/tracing/

- Adds context of time
- Adds hierarchy of services involved

## Spans

- Single operation 
- Contain information about which trace they belong to
- Join together related spans to reconstruct entire trace of a request