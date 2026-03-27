# Dynamic Thread Group, Auto Correlation, and Boundary Extractor for JMeter

This repository provides a single JMeter extension jar:

- `00_ApacheJMeter_enhanced_features.jar`

Copy this one jar into your JMeter `lib/ext/` folder to enable:

- Dynamic Load Thread Group
- Auto Correlation
- Boundary Extractor support
- JSON and Regex assisted correlation flows
- Stock-style startup result file popup behavior fix

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

This feature helps you capture dynamic values from responses and use them in later requests.

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
- helps you find the right value from request or response data
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

1. Run your script or send a request.
2. Open the response or request area where the dynamic value appears.
3. Select the exact value you want to capture.
4. Right-click and choose the auto correlation option.
5. Choose the extractor type you want.
6. Review the detected match and variable details.
7. Add the extractor to the test plan.
8. Replace the future hardcoded value with the created variable.
9. Run the script again and verify the value is now dynamic.

### Best Use Cases

- login token capture
- session handling
- extracting IDs from create-order or create-user responses
- linking one API request to the next request automatically

## How To Use Boundary Extractor

### Step-by-Step

1. Find the dynamic value in the response.
2. Identify the text just before the value.
3. Identify the text just after the value.
4. Open the extraction flow from the UI.
5. Choose `Boundary Extractor`.
6. Confirm the left boundary and right boundary.
7. Set a variable name.
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

Use Auto Correlation or Boundary/Regex extraction to capture a token returned after login, then use that variable in the Authorization header of the next request.

### Example 2: Order Creation Flow

Create an order, capture the generated order ID from the response, then use that ID in get-order, update-order, or cancel-order requests.

### Example 3: Spike Test

Use Dynamic Load Thread Group to simulate a sudden increase in users after a quiet period and verify whether the application remains stable.

### Example 4: Long Stability Test

Use the Soak scenario to run moderate traffic for hours and observe memory, response times, and system degradation.

## Included Fix

This jar also includes a fix for result file startup behavior so JMeter keeps stock-style overwrite and append prompting behavior instead of showing unexpected prompts from disabled listeners.
## File Integrity

- SHA-256: `478252444b87aec2221f6f09b56198ddccbea7bf27d0c7bf4e8abf928c5ba4ab`
