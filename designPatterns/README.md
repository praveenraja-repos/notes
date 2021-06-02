# Microservice Design Patterns

## SEGA Design Patterns

This pattern can be implemented in two ways

- Choreography
- Orchestration

### __Choreography__
Choreography is an event-driven approach. When using choreography, there isn’t a central coordinator telling the saga participants what to do. Instead, the saga participants subscribe to each other’s events and respond accordingly. When a service updates its data, it simply emits a domain event announcing what it has done. Other services subscribe to those events, which trigger updates that emit additional events

#### Drawbacks
- Workflow can become confusing when adding new steps, as it's difficult to track which saga participants listen to which commands.
- There's a risk of cyclic dependency between saga participants because they have to consume each other's commands.
- Integration testing is difficult because all services must be running to simulate a transaction.


### __Orchestration__

Orchestration uses a saga orchestrator that tells the saga participants what to do. The saga orchestrator communicates with the participants using request/asynchronous response-style interaction. To execute a saga step, it sends a command message to a participant telling it what operation to perform. After the saga participant has performed the operation, it sends a reply message to the orchestrator. The orchestrator then processes the reply message and determines which saga step to perform next. 

#### Drawbacks

- Additional design complexity requires an implementation of a coordination logic.
- There's an additional point of failure, because the orchestrator manages the complete workflow.
