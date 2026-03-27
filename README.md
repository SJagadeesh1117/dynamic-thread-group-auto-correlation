# Dynamic Thread Group and Auto Correlation for JMeter

This repository provides a single JMeter extension jar:

- `00_ApacheJMeter_enhanced_features.jar`

Copy this one jar into your JMeter `lib/ext/` folder to enable:

- Dynamic Load Thread Group
- Auto Correlation helpers
- Stock-style startup result file popup behavior fix

## Who This Is For

This jar is useful if you want to:

- create realistic load profiles without manually building many thread groups
- speed up correlation work while scripting JMeter test plans
- use one drop-in jar instead of modifying multiple JMeter source files

## What You Get

### 1. Dynamic Load Thread Group

This feature adds a custom thread group to JMeter for building different load patterns more easily.

Use it when you want to:

- run a quick validation with a small number of users and loops
- perform smoke testing after deployment
- create steady load for normal performance testing
- create stress load to find system limits
- create soak tests for long-duration stability checks
- create spike tests to simulate sudden traffic jumps
- configure custom ramp-up, hold, and ramp-down phases visually

Typical use cases:

- validate that a new API deployment is healthy before full testing
- simulate business-hour traffic with gradual ramp-up and ramp-down
- check how a system behaves during sudden peak traffic
- keep a service under load for hours to detect memory leaks or degradation

### 2. Auto Correlation

This feature helps extract dynamic values from responses and apply them back into your JMeter requests faster.

Use it when you want to:

- capture dynamic IDs, tokens, session values, and reference numbers
- create regex, boundary, or JSON extractor logic more quickly
- reduce repetitive manual correlation work while debugging scripts
- correlate values directly from JMeter UI locations where you inspect requests and responses

Typical use cases:

- session token extraction after login
- order ID or transaction ID capture from API responses
- request chaining where one response value is needed in the next sampler
- faster scripting of large workflows with many dynamic values

## Main Capabilities

### Dynamic Load Thread Group

- Available directly from JMeter thread group menu
- Includes validation, smoke, load, stress, soak, spike, and custom scenarios
- Lets you configure load phases visually
- Includes a live chart-style preview of the load profile

### Auto Correlation

- Start correlation from View Results Tree related UI
- Supports regex, boundary, and JSON extractor creation
- Helps detect surrounding boundaries automatically
- Supports navigation when a value appears multiple times
- Shows match source such as body or headers where relevant
- Adds extractor logic back into the test plan faster

## Installation

### Prerequisites

- Apache JMeter 5.6.3
- Access to your JMeter installation folder

### Steps

1. Close JMeter completely.
2. Download `00_ApacheJMeter_enhanced_features.jar` from this repository.
3. Open your JMeter installation folder.
4. Go to `lib/ext/`.
5. Copy `00_ApacheJMeter_enhanced_features.jar` into `lib/ext/`.
6. Start JMeter again.

## Important Notes

- This is a single drop-in jar.
- Put it in `lib/ext/`, not in `lib/`.
- Do not rename the jar unless you have a specific reason.
- Restart JMeter after copying the jar.
- If JMeter was already open while copying the jar, the features will not load until restart.

## How To Verify It Loaded

After starting JMeter:

- check Thread Group menu for the Dynamic Load Thread Group option
- use your JMeter UI flow where auto correlation is available and confirm the correlation actions appear

## File Integrity

- SHA-256: `478252444b87aec2221f6f09b56198ddccbea7bf27d0c7bf4e8abf928c5ba4ab`
