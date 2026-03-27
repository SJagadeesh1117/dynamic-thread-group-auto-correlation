# Dynamic Thread Group, Auto Correlation, and Boundary Extractor for JMeter

This repository provides a single JMeter extension jar:

- `00_ApacheJMeter_enhanced_features.jar`

Copy this one jar into your JMeter `lib/ext/` folder to enable:

- Dynamic Load Thread Group
- Auto Correlation
- Boundary Extractor support
- JSON and Regex assisted correlation flows

## What This Jar Is For

This jar is useful if you want to:

- create realistic load patterns without building multiple manual thread groups
- correlate dynamic response values faster while scripting JMeter tests
- create extractors from the JMeter UI with less manual work
- use a single drop-in jar instead of changing many JMeter files

## Features Included

### 1. Dynamic Load Thread Group

This feature adds a custom thread group that helps you create different performance test patterns quickly.

You can use it for:

- validation testing
- smoke testing
- normal load testing
- stress testing
- soak testing
- spike testing
- custom phase-based load profiles

Why it helps:

- no need to manually build many thread groups for different test types
- easier ramp-up, steady-state, and ramp-down control
- easier to explain and maintain test plans
- useful for both beginners and advanced JMeter users

### 2. Auto Correlation

This feature helps you capture dynamic values from recorded traffic and use them in later requests without first running the script manually.

You can use it for:

- session IDs
- auth tokens
- transaction IDs
- order IDs
- reference numbers
- dynamic headers
- request values that change on every run

Why it helps:

- reduces manual extractor creation work
- speeds up scripting
- helps you find the right value from recorded request or header data
- makes test plan maintenance easier

### 3. Boundary Extractor Support

This feature helps you extract values using left and right boundaries.

You can use it when:

- regex is too complex for a simple extraction
- the response has a stable text pattern before and after the value
- you want a simpler and more readable extractor

Examples:

- extract token between `"token":"` and `"`
- extract order id between `orderId=` and `&`
- extract session value between two known strings in HTML, JSON, or text responses

Why it helps:

- easier than regex for many common cases
- more readable for new users
- faster to troubleshoot in many scripts

## Supported Extraction Flows

This jar helps with these extractor styles:

- Boundary Extractor
- Regular Expression Extractor
- JSON Extractor

## Installation

### Prerequisites

- Apache JMeter 5.6.3
- access to your JMeter installation folder

### Step-by-Step Installation

1. Close JMeter completely.
2. Download `00_ApacheJMeter_enhanced_features.jar` from this repository.
3. Open your JMeter installation folder.
4. Open the `lib/ext/` folder inside JMeter.
5. Copy `00_ApacheJMeter_enhanced_features.jar` into `lib/ext/`.
6. Start JMeter again.

## Important Installation Notes

- This is a single drop-in jar.
- Put it in `lib/ext/`, not in `lib/`.
- Do not place it in `bin/`.
- Restart JMeter after copying the jar.
- If JMeter is already running, the new features will not appear until restart.

## How To Confirm The Jar Loaded

After JMeter starts:

1. Open the Thread Group menu.
2. Check whether `Dynamic Load Thread Group` appears.
3. Open places where you inspect requests and responses.
4. Check whether the auto correlation related options are available.

## How To Use Dynamic Load Thread Group

### Step-by-Step

1. Open JMeter.
2. Right-click your Test Plan.
3. Go to `Add -> Threads (Users)`.
4. Select `Dynamic Load Thread Group`.
5. Choose the scenario that matches your test goal.
6. Configure users, duration, loops, or phases as needed.
7. Review the load profile preview.
8. Add your samplers under this thread group.
9. Run the test.

### Which Scenario To Choose

- Validation: use this for quick checks with small user count and loops
- Smoke: use this after deployment to confirm the application is reachable and stable
- Load: use this for expected day-to-day traffic
- Stress: use this to push beyond expected load and find breaking points
- Soak: use this for long-running stability testing
- Spike: use this for sudden traffic increase testing
- Custom: use this when you want full control over phases

## How To Use Auto Correlation

### Step-by-Step

1. Add `View Results Tree` under `HTTP(S) Test Script Recorder` before recording.
2. Start recording your flow.
3. Perform the business flow you want to capture in the browser or client.
4. Let JMeter save the recorded requests and responses into `View Results Tree`.
5. Stop recording.
6. Open the recorded request or request headers where the dynamic value appears.
7. Select the exact value.
8. Right-click and choose `Auto Correlation`.
9. Review the place where the tool found the value and check the detected boundaries.
10. Create the correlation from that result.
11. Use the generated variable in the request that needs the dynamic value.

### Best Use Cases

- login token capture
- session handling
- extracting IDs from create-order or create-user responses
- linking one API request to the next request automatically

### Important Note

- you do not need to run the recorded script first
- the feature works from the values stored during recording in `View Results Tree`
- this is especially useful for correlating request values and request headers directly after recording

## How To Use Boundary Extractor

### Step-by-Step

1. Open `View Results Tree`.
2. Go to the `Response` tab for the recorded sampler.
3. Select the value you want to extract.
4. Right-click and choose `Boundary Extractor`.
5. Let the feature automatically detect the left and right boundaries.
6. Review the generated boundaries.
7. Set the variable name if needed.
8. Add the extractor to the correct sampler.
9. Use `${variableName}` in the next request where needed.

### When Boundary Extractor Is Better Than Regex

- when the surrounding text is simple and fixed
- when you want easier maintenance
- when you want a cleaner extractor for new team members to understand

## How To Use Regex Extractor

### Step-by-Step

1. Select the dynamic value from the response.
2. Open the extraction flow.
3. Choose `Regex Extractor`.
4. Review or edit the generated regex pattern.
5. Set the variable name and default value.
6. Add the extractor.
7. Use the generated variable in later requests.

## How To Use JSON Extractor

### Step-by-Step

1. Run a sampler that returns JSON.
2. Open the response.
3. Select the value you want to correlate.
4. Open the extraction flow.
5. Choose `JSON Extractor`.
6. Review the detected JSON path.
7. Set the variable name.
8. Add the extractor.
9. Reuse that variable in later requests.

## Practical Examples

### Example 1: Login Token

Record the login flow with `HTTP(S) Test Script Recorder`, keep the recorded entries in `View Results Tree`, then select the token from the recorded request or headers and use `Auto Correlation` to generate the correlation.

### Example 2: Order Creation Flow

Record an order creation flow, then open the recorded response in `View Results Tree`, right-click the generated order ID, choose `Boundary Extractor`, and use the created variable in get-order, update-order, or cancel-order requests.

### Example 3: Spike Test

Use Dynamic Load Thread Group to simulate a sudden increase in users after a quiet period and verify whether the application remains stable.

### Example 4: Long Stability Test

Use the Soak scenario to run moderate traffic for hours and observe memory, response times, and system degradation.

## File Integrity

- SHA-256: `478252444b87aec2221f6f09b56198ddccbea7bf27d0c7bf4e8abf928c5ba4ab`
