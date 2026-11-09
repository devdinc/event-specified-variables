# Event-specified Variables

Read and modify Skript variables against an explicitly selected event context. This is useful when a variable's value should be associated with a different event object than the current one.

## Requirements

- Skript 2.15+
- skript-reflect 2.6+

## Installation

```
package install https://github.com/devdinc/event-specified-variables
```

## Syntax

```skript
variable %string% with custom-event [%object%]
%$-objects% with custom-event [%object%]
```

The first form accepts a variable name as text. The second accepts a Skript variable expression. The optional custom event object selects the event context used for the variable operation; if omitted, the current event is used.

The expression supports the normal variable change operations: get, set, add, remove, remove all, delete, and reset. List variables can be addressed with a `::*` suffix.

## Examples

```skript
# Read a variable in a supplied event context
set {_value} to variable "player-score" with custom-event {_event}

# Set a variable in that event context
set variable "player-score" with custom-event {_event} to 10

# Use a variable expression instead of a string name
add 1 to {_score} with custom-event {_event}

# Work with a list variable
set variable "round-results::*" with custom-event {_event} to 10, 20, 30
```

When the custom event argument is omitted, operations use the current event context.

## Source and tests

- Implementation: `src/event-specified-variables.sk`
- Tests: `-tests/`
