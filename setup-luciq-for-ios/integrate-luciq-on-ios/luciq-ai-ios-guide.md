# Guide for AI Coding Agents to Integrate Luciq on iOS

### ⚠️ UNIVERSAL EXECUTION RULES ⚠️

**Critical Rules - Apply to ALL Platforms:**

* NEVER skip WAIT instructions - always get user confirmation before proceeding
* NEVER auto-execute optional steps - user must explicitly select them
* ALWAYS fetch latest SDK version before integration (DO NOT use placeholders like 1.0.0)
* ALL API parameters must be included (can be nil/null) - never omit parameters

**Execution Guidelines:**

* Be specific and concise — save tokens by being to the point
* Don't create documentation files — only code files required for integration
* Implement mandatory steps sequentially — complete each before moving to the next
* Prompt user with current step — describe what's happening, then proceed when done
* Only ask for optional steps after mandatory ones — show numbered list for selection
* Use numbered lists for all options — makes selection easier (e.g., "Select 1", "Select 2")
* Add wrap up step — execute validation only when user selects "Wrap up & validate"
* Check documentation first — confirm API availability before getting creative beyond examples

**Official Documentation:**

* Main docs: [https://docs.luciq.ai/](https://docs.luciq.ai/)
* Always check official docs when unsure about API signatures or platform specifics

***

### Integration Workflow Overview

{% stepper %}
{% step %}
### MANDATORY STEPS — Overview

Step 1: Collect Required Information

* 1A: Get App Token (MCP or Manual)
* 1B: Determine Integration Method
* 1C: Apply Default Config (Inform + Opt-in Customize)

Step 2: Add SDK Dependency (Platform-Specific)

* Fetch latest version from GitHub API

Step 3: Initialize the SDK (Platform-Specific)

* Default: shake + floatingButton

Step 3B: Configure Network Interception \[ANDROID ONLY]

* Enable unified network interception in Gradle
{% endstep %}

{% step %}
### DEFAULT CONFIG (Auto-Applied)

Applied automatically (customizable via opt-in):

* Network Logging: enabled + common field masking
* Screenshot Masking: iOS=maskNothing, Android=all
* Symbolication Upload: automatic
* User Identification: skip
{% endstep %}

{% step %}
### VERIFICATION

Wrap up & validate: Build → Test → Verify Dashboard
{% endstep %}
{% endstepper %}

***

### Step 1 — Collect Required Information \[MANDATORY]

{% stepper %}
{% step %}
#### 1A: Get App Token

Check MCP server first:

```
IF Luciq MCP server is installed:
  1. Fetch all tokens with app names using MCP tools
  2. Display tokens to user in numbered list with app names
  3. Ask: "Which app token would you like to use?"
  4. WAIT for selection
  5. Store selected token
ELSE:
  1. Display to user: "To integrate Luciq SDK, you'll need your App Token."
  2. Display to user:
     "📍 Find your token: Luciq Dashboard → Settings → SDK Integration"
  3. Display on new line with indentation:
     "   Dashboard URL: https://dashboard.luciq.ai"
  4. Ask: "Please provide your Luciq App Token:"
  5. WAIT for user to provide token
  6. Validate token format (non-empty, alphanumeric)
  7. Store token for later use
END IF
```

Validation:

* Token should be non-empty
* Typically 32–40 character hexadecimal string
* If invalid format, warn user but proceed

```
```
{% endstep %}

{% step %}
#### 1B: Determine Integration Method

Auto-detection logic (iOS):

* Detect `Podfile` → CocoaPods
* Detect `Cartfile` → Carthage
* Detect SPM packages in `.xcodeproj` → SPM
* None → Manual

```
DETECT package managers in project:
  - Count how many are found

IF exactly ONE package manager detected:
  Inform user: "Detected [PackageManager], will use this for integration"
  Store integration_method
  Proceed to Step 2
ELSE IF multiple or zero detected:
  Display platform-specific menu:
    1. Swift Package Manager (SPM) [Recommended]
    2. CocoaPods
    3. Carthage
    4. Manual (XCFramework)
  WAIT for user selection
  Store integration_method
  Proceed to Step 2
END IF
```
{% endstep %}

{% step %}
#### 1C: Apply Default Configuration (Inform + Opt-in)

Default configuration is applied automatically. Inform the user:

```
Applying default configuration:
  • Invocation: shake + floatingButton
  • Network logging: enabled with common field masking
  • Screenshot masking:
      - iOS: maskNothing (customize per privacy settings)
      - Android: all types (text inputs, labels, media)
  • Symbolication: automatic upload enabled
  • APM (Android): enabled
  • User identification: skip (can add later)

Would you like to customize any of these settings? (yes/no)
```

Store default configuration:

```
invocation_events = [shake, floatingButton]
network_logging_enabled = true
network_masking_enabled = true
predefined_headers_to_mask = ["Authorization", "Cookie", "X-API-Key", "token"]
predefined_body_fields_to_mask = ["password", "token", "ssn"]
auto_masking_types:
  iOS: maskNothing
  Android: [textInputs, labels, media]
symbolication_upload = enabled
repro_steps_config = skip
user_identification = skip
```

If user chooses to customize, run the customization loop:

1. Which setting to customize? (numbered list)
2. WAIT for selection
3. Apply customization
4. Redisplay updated configuration
5. Ask if they want to customize anything else — repeat until done
{% endstep %}

{% step %}
#### 1D: Fastlane Detection (iOS only)

Auto-detection:

```
Search for Fastlane configuration:
  - Look for Fastfile in project root or fastlane/ directory
  - Check if it contains archive/gym lanes

IF Fastlane detected:
  Store fastlane_detected = true
  Inform user: "Fastlane detected - will configure dSYM upload via Fastlane plugin"
ELSE:
  Store fastlane_detected = false
  Inform user: "Will configure dSYM upload via Xcode Archive Post-actions"
END IF

Proceed to Step 2
```
{% endstep %}
{% endstepper %}

***

### Step 2 — Add SDK Dependency \[MANDATORY - iOS]

> MUST FETCH LATEST VERSION FIRST: https://api.github.com/repos/luciqai/luciq-ios-sdk/releases/latest\
> Extract version from "tag\_name" (e.g., "19.1.0") and store it. DO NOT use placeholders like "1.0.0" or "latest".

{% stepper %}
{% step %}
#### If integration\_method == spm (SPM - REQUIRED programmatic changes)

Important: When adding the SDK via SPM, you MUST update BOTH:

* Package.swift
* project.pbxproj

Xcode UI (manual) for reference:

1. File → Add Package Dependencies...
2. Enter URL: https://github.com/luciqai/luciq-ios-sdk
3. Select "Exact Version" and enter \<FETCHED\_VERSION>
4. Add "Luciq" product to your target

Programmatic changes (agent MUST modify project.pbxproj):

* Add entries to PBXBuildFile, PBXFrameworksBuildPhase, PBXNativeTarget.packageProductDependencies, PBXProject.packageReferences.
* Add XCRemoteSwiftPackageReference section with: repositoryURL = "https://github.com/luciqai/luciq-ios-sdk" requirement = { kind = exactVersion; version = \<FETCHED\_VERSION>; }
* Add XCSwiftPackageProductDependency for productName = Luciq

Also update Package.swift:

{% code title="Swift" %}
```swift
// In Package.swift dependencies array:
dependencies: [
    .package(url: "https://github.com/luciqai/luciq-ios-sdk", exact: "<FETCHED_VERSION>")
],

// In target dependencies:
.target(
    name: "YourTarget",
    dependencies: [
        .product(name: "Luciq", package: "luciq-ios-sdk")
    ]
)
```
{% endcode %}

ID generation notes:

* Use unique 24-character hexadecimal IDs consistent with project file

````
{% endstep %}

{% step %}
### If integration_method == cocoapods

Add to Podfile:

```ruby
pod 'Luciq', '~> <MAJOR_VERSION>'  # e.g., '~> 19.0'
````

Then run:

```bash
pod install
```

\{% endstep %\}

\{% step %\}

#### If integration\_method == carthage

Add to Cartfile:

```

binary "https://raw.githubusercontent.com/luciqai/luciq-ios-sdk/main/Luciq.json"
```

Then run:

```bash
carthage update --platform iOS
```

\{% endstep %\}

\{% step %\}

#### If integration\_method == manual (XCFramework)

1. Download: https://github.com/luciqai/luciq-ios-sdk/releases/latest/download/Luciq-XCFramework.zip
2. Unzip to reveal Luciq.xcframework
3. Drag into Xcode project → Frameworks, Libraries, and Embedded Content
4. Select "Embed & Sign" \{% endstep %\} \{% endstepper %\}

***

### Step 3 — Initialize the SDK \[MANDATORY - iOS]

> ALWAYS use `import LuciqSDK` (NOT `import Luciq`)\
> SDK initialization MUST be the FIRST line in init()/didFinishLaunchingWithOptions.\
> Use `exact` SPM version requirement when adding package.

\{% stepper %\} \{% step %\}

#### Where to place initialization

* SwiftUI: App struct's `init()` — AS THE FIRST LINE
* UIKit: AppDelegate's `application(_:didFinishLaunchingWithOptions:)` — AS THE FIRST LINE

Examples:

SwiftUI

```swift
import SwiftUI
import LuciqSDK

@main
struct YourApp: App {
    init() {
        // MUST be FIRST
        Luciq.start(withToken: "<APP_TOKEN>", invocationEvents: [.shake, .floatingButton])
        // Other initialization...
    }

    var body: some Scene {
        WindowGroup {
            ContentView()
        }
    }
}
```

UIKit (AppDelegate)

```swift
import UIKit
import LuciqSDK

@main
class AppDelegate: UIResponder, UIApplicationDelegate {
    func application(_ application: UIApplication,
                     didFinishLaunchingWithOptions launchOptions: [UIApplication.LaunchOptionsKey: Any]?) -> Bool {
        // MUST be FIRST
        Luciq.start(withToken: "<APP_TOKEN>", invocationEvents: [.shake, .floatingButton])
        // Other initialization...
        return true
    }
}
```

\{% endstep %\}

\{% step %\}

#### Invocation Events Syntax

Default invocation events: `[.shake, .floatingButton]`

Examples:

```swift
// Default
Luciq.start(withToken: "<APP_TOKEN>", invocationEvents: [.shake, .floatingButton])

// Screenshot only
Luciq.start(withToken: "<APP_TOKEN>", invocationEvents: [.screenshot])

// All events
Luciq.start(withToken: "<APP_TOKEN>", invocationEvents: [.shake, .screenshot, .floatingButton])

// None (manual only)
Luciq.start(withToken: "<APP_TOKEN>", invocationEvents: [])
```

Mapping:

* none → \[]
* single → \[selected]
* multiple → \[event1, event2, ...] \{% endstep %\}

\{% step %\}

#### Step 3B — Add Info.plist Permissions

Fetch app name from Info.plist (CFBundleDisplayName or CFBundleName) or project.pbxproj (PRODUCT\_NAME) and add if not present:

```xml
<key>NSMicrophoneUsageDescription</key>
<string><APP_NAME> needs access to your microphone so you can attach voice notes.</string>
<key>NSPhotoLibraryUsageDescription</key>
<string><APP_NAME> needs access to your photo library so you can attach images.</string>
```

Implementation:

1. Locate Info.plist
2. Add NSMicrophoneUsageDescription if missing
3. Add NSPhotoLibraryUsageDescription if missing
4. Inform user of added permissions

````

</div>

</div>

---

## Optional Steps (Menu presented only after mandatory steps complete)

After mandatory steps, present a numbered menu for optional steps (user must select). Example menu:

1. Configure optional features  
2. Wrap up & validate

Do NOT proceed with wrap up unless user selects option 2.

Optional features include:
* Configure Network Logging (Optional Step 1)
* Mask Repro Step Screenshots (Optional Step 2)
* Configure Repro Steps Mode (Optional Step 3)
* Add User Identification (Optional Step 4)
* Upload Symbolication Files (Optional Step 5)

All optional interactions must follow the universal rules: WAIT where required, don’t auto-execute optional flows.

---

## Optional Step 1 — Configure Network Logging (iOS)

Concepts:
* Purpose: Capture network requests/responses and optionally mask sensitive data
* Masking code MUST be placed AFTER SDK initialization
* Use Set<String> for O(1) field lookup
* Body masking should use a recursive function to handle nested JSON

Default (applied if config_mode == default):
* Headers: ["Authorization", "Cookie", "X-API-Key", "token"]  
* Body fields: ["password", "token", "ssn"]

Disable automatic capture (custom mode only — call BEFORE Luciq.start()):

```swift
NetworkLogger.disableAutomaticCapturingOfNetworkLogs()
````

Mask Sensitive Data (AFTER Luciq.start()) — SwiftUI example:

```swift
NetworkLogger.setRequestObfuscationHandler { request in
    var mutableRequest = (request as NSURLRequest).mutableCopy() as! NSMutableURLRequest

    // Mask headers
    for header in headersToMask {
        if mutableRequest.value(forHTTPHeaderField: header) != nil {
            mutableRequest.setValue("*****", forHTTPHeaderField: header)
        }
    }

    // Mask body (recursive)
    if let body = mutableRequest.httpBody,
       let jsonObject = try? JSONSerialization.jsonObject(with: body) {
        let maskedObject = Self.maskFields(in: jsonObject, fieldsToMask: bodyFieldsToMask)
        if let newBody = try? JSONSerialization.data(withJSONObject: maskedObject) {
            mutableRequest.httpBody = newBody
        }
    }

    return mutableRequest.copy() as! URLRequest
}
```

Recursive helper (as provided earlier) must handle dictionaries and arrays.

Key points:

* Masking MUST be configured AFTER Luciq.start()
* Use Sets for performance
* Handle nested JSON recursively

***

### Optional Step 2 — Mask Repro Step Screenshots (iOS)

Default: `.maskNothing`

API examples:

```swift
// Default
Luciq.setAutoMaskScreenshots(.maskNothing)

// Text inputs only
Luciq.setAutoMaskScreenshots([.textInputs])

// Labels only
Luciq.setAutoMaskScreenshots([.labels])

// Text inputs + labels
Luciq.setAutoMaskScreenshots([.textInputs, .labels])

// All types
Luciq.setAutoMaskScreenshots([.textInputs, .labels, .media])
```

Available mask types:

* `.maskNothing`
* `.textInputs`
* `.labels`
* `.media`

SwiftUI auto-masking:

* Changing masked types from `.maskNothing` automatically masks SwiftUI views
* To disable auto-masking: `Luciq.autoMaskSwiftUIViews = false`

Present a numbered menu for the user to select which elements to mask (1–7 as in original workflow). WAIT for selection.

***

### Optional Step 3 — Configure Repro Steps Mode (iOS)

Present a multiple-selection menu:

1. Bug Reporting
2. Crash Reporting
3. Session Replay
4. All products
5. None
6. Keep defaults

Apply mapping:

```swift
// Example: enable bug and session replay
Luciq.setReproStepsFor(.bug, with: .enable)
Luciq.setReproStepsFor(.sessionReplay, with: .enable)
Luciq.setReproStepsFor(.crash, with: .enabledWithNoScreenshots)  // if not selected
```

Selected → `.enable` (with screenshots)\
Not selected → `.enabledWithNoScreenshots` (without screenshots)

WAIT for user input and apply platform-specific calls accordingly.

***

### Optional Step 4 — Add User Identification (iOS)

Present numbered choices:

1. Using email
2. Using user ID
3. Using both email and ID
4. Skip

If user skips, end flow. Otherwise, identify login/logout flows and instrument:

Identify after successful authentication and before navigation:

```swift
Luciq.identifyUser(
    withID: String?,     // can be nil
    email: String?,      // can be nil
    name: String?        // can be nil
)
```

Examples:

* Email only: `Luciq.identifyUser(withID: nil, email: user.email, name: user.name)`
* ID only: `Luciq.identifyUser(withID: user.id, email: nil, name: user.name)`
* Both: `Luciq.identifyUser(withID: user.id, email: user.email, name: user.name)`

Logout call (call BEFORE clearing session/data):

```swift
Luciq.logOut()
```

WAIT for user to confirm placements and apply code.

***

### Optional Step 5 — Upload dSYM Files (iOS)

This step is configured automatically based on Fastlane detection (Step 1D). Present options:

1. Automatic (recommended) — Fastlane plugin or Run Script Build Phase
2. Manual — upload through dashboard
3. Skip

If Fastlane detected (fastlane\_detected == true) — Fastlane plugin approach:

```bash
fastlane add_plugin luciq_official
```

In Fastfile (archive lane):

```ruby
lane :archive do
  gym(
    scheme: "<SCHEME_NAME>",
    archive_path: "./build/<APP_NAME>.xcarchive"
  )
  luciq_official(
    api_token: "<APP_TOKEN>",
    dsym_array_paths: ["./build/<APP_NAME>.xcarchive/dSYMs/<APP_NAME>.app.dSYM"]
  )
end
```

Plugin params:

* api\_token (required)
* dsym\_array\_paths (required for local archives)
* eu (optional)
* end\_point (optional)

If Fastlane not detected — add Run Script Build Phase (agent MUST modify project.pbxproj):

Add a PBXShellScriptBuildPhase named "Upload dSYM to Luciq" with shellScript:

```sh
SCRIPT_SRC=$(find "$PROJECT_DIR" -name 'Luciq_dsym_upload.sh' | head -1)
if [ ! "${SCRIPT_SRC}" ]; then
  echo "Luciq: err: upload script not found. Download from Luciq dashboard."
  exit 0
fi
APP_TOKEN="<APP_TOKEN>"
source "${SCRIPT_SRC}"
```

Notes:

* Use `exit 0` when script not found to avoid build failures
* Replace `<APP_TOKEN>` with token from Step 1A

Agent must add the build phase to PBXNativeTarget.buildPhases as LAST item.

***

### Step 4 — Verification & Testing (Wrap up & validate) \[USER-INITIATED ONLY]

This step must only run when the user explicitly selects "Wrap up & validate".

Display summary and options:

```
✅ Luciq SDK integration complete!

Platform: iOS
SDK Version: <version>
Integration Method: <SPM/Pods/Carthage/Manual>

Configuration:
  • App Token: <first 8 chars>...
  • Invocation Events: <configured events>
  • Network Logging: <enabled/disabled>
  • Network Masking:
      - Headers: <list or none>
      - Body Fields: <list or none>
  • Screenshot Masking: <types or none>
  • Symbolication Upload: <automatic/manual/skip>
  • User Identification: <configured or not configured>

Next Steps - Select an option:
1. Configure optional features
2. Wrap up & validate
```

WAIT for selection. Do NOT proceed to build verification unless user selects option 2.

#### Build Verification (Only when requested)

Run iOS build verification command:

```bash
xcodebuild -project YourProject.xcodeproj \
           -scheme YourScheme \
           -configuration Debug \
           -destination 'platform=iOS Simulator,name=iPhone 15 Pro' \
           build
```

Expected: \*\* BUILD SUCCEEDED \*\*

Common iOS build errors and fixes:

* "no such module 'Luciq'" → used `import Luciq` instead of `import LuciqSDK`
* "version not found" → invalid SPM version — verify releases/latest
* "Missing package product 'Luciq'" → add "Luciq" product to target

#### Runtime Testing (Manual)

1. Build and run the app on simulator/device
2. Trigger Luciq using configured invocation method:
   * Shake: Hardware → Shake (Cmd+Ctrl+Z in simulator)
   * Screenshot: take screenshot
   * Floating Button: tap overlay
3. Verify Luciq UI appears
4. Submit test bug report
5. Check Luciq dashboard: https://dashboard.luciq.ai

#### Final Summary (after successful validation)

Display:

```
✅ Luciq SDK successfully integrated and validated!

Platform: iOS
SDK Version: <version>
Integration Method: <SPM/Pods/Carthage/Manual>

Configuration: <as above>

Build Status: ✅ SUCCEEDED

Next Steps:
  • Run the app and test SDK invocation
  • Submit a test report
  • Verify report in Luciq dashboard
```

***

### Error Handling & Troubleshooting (iOS highlights)

1. SDK Not Initializing
   * Verify token is correct
   * Check initialization code placement (App entry point)
   * Ensure `import LuciqSDK` is used
2. Network Logging Not Working
   * Ensure masking code is after `Luciq.start()`
   * Confirm NetworkLogger is available via `import LuciqSDK`
3. User Identification Not Showing
   * Verify identifyUser called after successful login and not with all nil params
4. Reports Not Appearing in Dashboard
   * Check internet, app token, and dashboard filters

iOS-specific errors:

* "Command SwiftCompile failed" — check imports and syntax (`import LuciqSDK`)
* "Fastlane dSYMs file is not found!" — ensure `dsym_array_paths` parameter when using local archives

***

### iOS Quick Reference

```swift
// ALWAYS use this import
import LuciqSDK

// Default initialization (shake + floatingButton)
Luciq.start(withToken: "token", invocationEvents: [.shake, .floatingButton])

// User identification
Luciq.identifyUser(withID: nil, email: "[email protected]", name: "John")

// Logout
Luciq.logOut()

// Screenshot masking (default: maskNothing)
Luciq.setAutoMaskScreenshots(.maskNothing)

// Network masking (AFTER start)
NetworkLogger.setRequestObfuscationHandler { request in
    // ... masking logic ...
}
```
{% endstep %}
{% endstepper %}
