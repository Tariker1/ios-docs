---
title: MCP - Tools
---

## **Overview**

The **Luciq MCP Server** provides four primary tools via JSON-RPC 2.0 that can be accessed directly in your IDE or via API. These tools help developers retrieve crash data, analyze trends, and debug faster, all from within AI-native IDEs like Cursor and Claude Code.

***

### **Tool 1:`listApplications`**

Retrieves a list of applications accessible to the authenticated developer

**Input Parameters**:

* `offset` (optional): Number of applications to skip (default: 0)
* `limit` (optional): Maximum number of applications to return (default: 10)
* `platform` (optional): Filter by platform
  * Valid values: `ios`, `android`, `react_native`, `flutter`

**Output**: JSON-RPC 2.0 response containing:

The `text` field contains JSON with an array of applications, each containing:

* `token` Application token identifier
* `created_at` Application creation timestamp
* `mode` Application mode (production, beta, staging, alpha, qa, development)
* `name` Application display name
* `slug` Application slug identifier
* `platform` Platform type (ios, android, react\_native, flutter)

<figure><img src="https://files.readme.io/77ff5c0752444b3324c25231392ff43e566bc3b08bc0bf5537817a7d3dd29447-List_Applications.png" alt="Luciq MCP Server in Cursor - List Applications" width="375"><figcaption><p>Luciq MCP Server in Cursor - List Applications</p></figcaption></figure>

**Example IDE Queries**

> “List all my iOS and Android apps.”
>
> "Show me applications for Android platform in Production."

**When to use it**

* To confirm connection and workspace access
* To identify your app slug before querying crash data

***

### **Tool 2:`listCrashes`**

Retrieves crash data for a specific application with advanced filtering and pagination

**Required Parameters**:

* `slug` Application slug identifier
* `mode` Application mode
  * Valid values: `beta`, `production`, `staging`, `alpha`, `qa`, `development`

**Optional Parameters**:

* `offset` Number of crashes to skip from the beginning (default: 0)
* `limit` Maximum number of crashes to return (default: 20, max: 100)
* `sort_by` Sort field (default: `last_occurred_at`)
  * Valid values: `last_occurred_at`, `occurrences_counter`, `affected_users_counter`, `max_app_version`, `min_app_version`, `severity`, `first_occurred_at`
* `direction` Sort direction - `asc` or `desc` (default: `desc`)

**Filter Parameters** (`filters` object):

* `date_ms` Date range filter for crash occurrence time
  * `gte` Start timestamp
  * `lte` End timestamp
* `status_id` Crash status IDs
  * `1`: Open crashes
  * `2`: Closed crashes
  * `3`: In-progress crashes
* `teams` Team IDs to filter by assigned team
* `app_versions` Application versions to filter by
* `devices` Device names to filter by
* `os_versions` OS versions to filter by
* `platform` Platform types
  * Valid values: `IOS`, `ANDROID`, `DART` (Flutter), `JAVASCRIPT` (React Native)
* `current_views` Current view/screen names to filter by

**Output**: JSON-RPC 2.0 response containing:

The `text` field contains JSON array with crash objects, each containing:

* `min_app_version` Minimum app version affected
* `max_app_version` Maximum app version affected
* `last_occurred_at` Last occurrence timestamp (milliseconds)
* `first_occurred_at` First occurrence timestamp (milliseconds)
* `affected_users_counter` Number of affected users
* `occurrences_counter` Total occurrence count
* `severity` Crash severity level
* `status_id` Status ID (1=open, 2=closed, 3=in\_progress)
* `number` Crash number identifier
* `exception` Exception message
* `crash_cause` Root cause of crash
* `crash_type` Type of crash (FATAL, ANR, etc..)
* `platform` Platform label (ANDROID, IOS, etc..)
* `current_view` Current view where crash occurred
* `team` Team details with name and ID
* `app_version` App version
* `signals` Crash signals (e.g., \["recent"])
* `exception_name` Exception name (iOS only)
* `merging` Merging status (if applicable)
* `package` Package name (Android only)
* `level` Crash level (critical, error, warning for non-fatal crashes)
* `path` File path (iOS/React Native only)

<figure><img src="https://files.readme.io/da24ed379d7fdabbfbb6a54e20484ba4b830266dc53cab3c0ebcc89f1f6729a0-List_Crashes.png" alt="Luciq MCP Server in Cursor - List Crashes" width="375"><figcaption><p>Luciq MCP Server in Cursor - List Crashes</p></figcaption></figure>

**Example IDE Queries**

> "Show me production crashes for my-app in the last 30 days"
>
> "List all open crashes for iOS platform"
>
> "Get crashes from staging environment"

**When to use it:**

* During triage to identify high-priority issues
* To review new crashes after a deployment

***

### **Tool 3:`crashDetails`**

Get detailed information about a specific crash

**Required Parameters**:

* `slug` Application slug identifier
* `mode` Application mode
  * Valid values: `beta`, `production`, `staging`, `alpha`, `qa`, `development`
* `number` Crash number identifier

**Output**: JSON-RPC 2.0 response containing:

The `text` field contains JSON with detailed crash information:

* `number` Crash number identifier
* `type` Crash type (AndroidCrash, iOSCrash, etc.)
* `last_occurred_at` Last occurrence timestamp (ISO 8601 format)
* `min_app_version` Minimum affected app version
* `max_app_version` Maximum affected app version
* `exception` Exception message
* `exception_name` Exception name (null for Android)
* `priority_id` Priority ID (-1 if not set)
* `status_id` Status ID (1=open, 2=closed, 3=in\_progress)
* `crash_cause` Root cause of crash
* `severity` Crash severity (null for non-fatal)
* `crash_type` Type of crash (FATAL, NON\_FATAL)
* `app_version` App version
* `threads_count` Number of threads
* `stack_frames` Formatted stack frames with index, library, description, and type
* `sdk_version` SDK version
* `causes` Exception causes (null for Android non-fatal crashes)
* `package` Package name (Android only)
* `path` File path (iOS/React Native only)
* `team` Team details with name and ID
* `level` Crash level (critical, error, warning for non-fatal crashes)
* `ndk_info` NDK information (Android only)

<figure><img src="https://files.readme.io/ab736ff5b551b96704b7309bf72b048462603b8a6cb2f2d58c2aa1e437485477-Crash_Details.png" alt="Luciq MCP Server in Cursor - Crash Details" width="375"><figcaption><p>Luciq MCP Server in Cursor - Crash Details</p></figcaption></figure>

**Example IDE Queries**

> "Show me details for crash number 12 in production"
>
> "Get crash details for my-app staging crash #5"

**When to Use It:**

* To pinpoint root causes of critical crashes
* During debugging sessions with AI assistants
* When reviewing whether an issue has reoccurred

***

### **Tool 4:`crashPatterns`**

Retrieves aggregated crash pattern data for a specific crash.

**Required Parameters**:

* `slug` Application slug identifier
* `mode` Application mode
  * Valid values: `beta`, `production`, `staging`, `alpha`, `qa`, `development`
* `number` Crash number identifier
* `pattern_key` Type of pattern grouping
  * Valid values: `app_versions`, `devices`, `oses`, `current_views`, `app_status`, `experiments`

**Optional Parameters:**

* `sort_by` Field used for sorting (default: `occurrences_count`)
  * Valid values: `occurrences_count`, `last_seen`, `first_seen`
* `direction` Sorting direction (default: `desc`)
  * Valid values: `asc`, `desc`
* `filters` Optional filters for date range and attributes:
  * `date_ms` (object):
    * `gte` Start timestamp (milliseconds)
    * `lte` End timestamp (milliseconds)
  * `app_versions` Filter by specific app versions
  * `devices` Filter by device names
  * `os_versions` Filter by OS versions

**Output**: JSON-RPC 2.0 response containing:

* `total_occurrences_count` Total number of crash occurrences in all matching patterns
* `patterns_list` List of grouped crash patterns, each containing:
  * `value` The group value (e.g., device name, app version, OS version)
  * `occurrences_count` Number of occurrences for this group
  * `last_seen` Most recent occurrence timestamp (milliseconds)
  * `first_seen` Earliest occurrence timestamp (milliseconds)

<figure><img src="https://files.readme.io/3e4ef36ba00c84a760c2afc1493a335744b1ff7f746996bc1c66a6c5cfa13a35-Crash_Patterns.png" alt="Luciq MCP Server in Cursor - Crash Patterns" width="375"><figcaption><p>Luciq MCP Server in Cursor - Crash Patterns</p></figcaption></figure>

**Example IDE Queries**

> “Show crash patterns for crash #5 grouped by devices”
>
> “Get OS version distribution for crash 12 in production”
>
> “List app version patterns for my-app crash 30”

**When to use it**

* To identify device or OS-specific trends
* To understand the scope of a crash across different environments
* For regression monitoring after app updates or experiments

***

## **Error Handling**

**Authentication Errors**

* **Error Code**: `-32600-` Missing Email or Token headers
* **Error Code**: `-32701 -` Invalid email or token
* **Resolution**: Verify your authentication credentials and contact your administrator

**Application Access Errors**

* **Error**: "Application with slug 'X' and mode 'Y' not found or not accessible"
* **Resolution**: Ensure you have proper permissions for the requested application and mode

**General Errors**

* **Error Code**: `-32603-` Internal server error
* **Resolution**: Contact support team with error details
