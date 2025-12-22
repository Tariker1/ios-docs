---
title: dynamic-team-ownership
---

The GitHub CODEOWNERS integration allows Luciq to automatically generate and maintain Crashes team ownership rules based on the `CODEOWNERS` file in your GitHub repository.

Instead of manually configuring file paths and assigning them to teams, Luciq fetches and syncs your CODEOWNERS file to ensure accurate, up-to-date ownership rules at scale.

## How It Works?

{% stepper %}
{% step %}
Once connected, Luciq fetches your `CODEOWNERS` file from your GitHub repository.
{% endstep %}

{% step %}
Parses all ownership patterns (paths, filenames).
{% endstep %}

{% step %}
Extracts teams (GitHub teams).
{% endstep %}

{% step %}
Lets you map teams to Luciq teams in a simple UI.
{% endstep %}

{% step %}
Generates crash ownership rules automatically based on this mapping.
{% endstep %}

{% step %}
Keeps rules in sync whenever your `CODEOWNERS` file changes on GitHub.
{% endstep %}
{% endstepper %}

This automation ensures that crash reports are always routed to the correct team without manual updates.

# Prerequisites

Before you begin:

* You must be an **Owner** or **Admin** or have permissions to manage Team Ownership.
* Your GitHub organization must allow installing GitHub apps.
* Your repository must contain a valid `CODEOWNERS` file.

***

## How to Set it up?

{% stepper %}
{% step %}
### Connect Luciq to GitHub

1.  Go to **Settings → Source Code Management** in the Luciq dashboard.<br>

    ![](<../assets/d3fb01a6e715953d1818898d6192995a62b9b5dcf737d44e1fd95221d137aaa9 initial_page_source_code_management.png>)
2. Click **Connect with GitHub**.
3.  Install Luciq App on GitHub or use the Installation ID if you already installed the App<br>

    ![](<../assets/258fe9b4b455f4d861fe233c4b80dfdf44fd1fb03fcd514f248e499395c07f7e Authenticate_Instabug.png>)


4. On GitHub; choose the repository you want Luciq to access.
5. Confirm permissions and return to Luciq.
{% endstep %}

{% step %}
## Select Repository, Branch, and Features

After connecting:

1. Choose the **repository** that contains your `CODEOWNERS` file.
2. Select the **branch** (e.g., `main`, `master`) where `CODEOWNERS` lives.
3. Select which features should access the integration:
   * `CODEOWNERS` file: allows you to define crashes team ownership by fetching and processing GitHub `CODEONWERS` file.
   * Resolve Agent: An AI-powered feature designed to automate the process of resolving mobile app crashes, enabling developers to resolve issues within minutes. [Learn more](https://docs.luciq.ai/docs/product-guides-smart-resolve#/)
4. Click Continue

![](<../assets/686f1062f274b7473d1d42049cb65522e9b152670897c5c3c68aa48486d05c18 Disabled_button.png>)

{% hint style="warning" %}
### Important Note

CODEOWNERS file feature requires only read-access to the `CODEOWNERS` file. It doesn't access your code or make any changes to your Repository.
{% endhint %}
{% endstep %}

{% step %}
## Review and confirm configuration

Luciq will let you review all the configuration settings including:

* Organization
* Repository
* Branch
* Enabled features

Then you can select whether you want to enable auto-sync for `CODEOWNERS` file or not. The auto-sync will automatically update team ownership rules once the `CODEOWNERS` file is updated on GitHub.

Finally once you confirm all settings and click **Connect**, Luciq will fetch and process the `CODEOWNERS` file

![](<../assets/91d65a33a8c3f103bea4bc7fdb27e9c20076bc7ec524e4d845d026f6e61df68c Finish.png>)
{% endstep %}

{% step %}
## Map `CODEOWNERS` to Luciq Teams

Luciq will extract all teams from your `CODEOWNERS` file (GitHub teams), then try to match the team names to Luciq teams. If matching is not successful then you will see a list of teams that need to be mapped to Luciq teams.

For each team:

1. Select a **Luciq team** that represents their ownership.
2. Save the mapping.
3. You can revisit and update this mapping anytime.

This mapping allows Luciq to convert `CODEOWNERS` rules into crash ownership rules.

![](<../assets/b51f6480cf4ac89f7dfc00db45312f36f4d06abd12e73cd1671d28a6e67a057a Configure_teams.png>)

{% hint style="warning" %}
Ownership rules are defined for mapped teams only. For Unmapped teams, their rules are defined once the mapping is complete.
{% endhint %}
{% endstep %}

{% step %}
## Automatic Rule Generation

Once mapping is complete:

* Luciq automatically generates **Team Ownership Rules** based on the parsed `CODEOWNERS` patterns.
* These rules appear on the **Team Ownership** page in your dashboard.
* Each rule references the associated Luciq team.

![](<../assets/bcfdabc16cbf5b7837ad796bacddc5462cbc14533c22d5d9e16cbae3193e5a6c Screenshot_2025 12 01_at_3.51.54_PM.png>)
{% endstep %}
{% endstepper %}

***

Automatic Syncing For `CODEOWNERS` File

Luciq keeps your rules in sync by:

* Monitoring your GitHub repository for any updates to `CODEOWNERS`.
* Re-processing the file when changes are detected.
* Updating ownership rules automatically.
* Sending email notifications to admins when:
  * Code ownership changes
  * New owners appear that need mapping
  * Rules are updated

{% hint style="warning" %}
**The `CODEOWNERS` file sync process runs once per day at 00:00 UTC.**
{% endhint %}

![](<../assets/20f45a64f43943f5f3b7c4ab71a7a48ae240604a03b174e4e9705acdbd02985a CODEOWNERS_Email_4_from_Figma.png>)

{% hint style="warning" %}
When automatic syncing is enabled, team ownership rules created by `CODEOWNERS` file cannot be edited. The only way to edit these rules is by updating the `CODEOWNERS` file on GitHub.
{% endhint %}

{% hint style="info" %}
If Automatic syncing is disabled, you will see a banner in the team ownership page to notify you that the `CODEOWNERS` file has changed on GitHub.

You can manually update ownership rules directly from the banner.
{% endhint %}

<figure><img src="../assets/98e5f214f3ba89849d720c3091df147789a30c32d70d1e049407325aa3517e67 Update_CODEOWNERS_from_Figma.png" alt=""><figcaption></figcaption></figure>

***

# Processing `CODEOWNERS` File

## Sample of CODEOWNERS file

`CODEOWNERS` file is a text file that contains paths and/or filenames assigned to certain teams in the following format:

{% code title="CODEOWNERS" %}
```
## App folders
/apps/web/ @frontend-team
/apps/mobile/ @mobile-team @qa-team

## Library and shared folders
/libs/api/ @backend-team
/libs/shared/ @platform-team

## Specific files
/README.md @documentation-team
/scripts/deploy.sh @devops-team

## Wildcard (valid pattern)
*/src/payment @payments-team
/src/checkout/* @checkout-team

## Specific file inside a path
/src/payments/invoice_service.py @payments-team
```
{% endcode %}

### iOS

Refer to [Matching iOS paths](https://docs.luciq.ai/docs/product-guides-team-ownership#/matching-pathspackages) for more information.

{% hint style="info" %}
Flutter and React-Native uses the same matching logic for iOS.
{% endhint %}

### Android

Unlike other platforms Android relies on packages (not paths) to assign crashes to teams. Hence, the paths in the `CODEOWNERS` file should include the package.

For example:

Assume the package is named: com.luciq.crashes; Then the path in the `CODEOWNERS` file should be: `/src/main/git/com/luciq/crashes`

### Supported Wildcard Patterns

On GitHub, you can use wildcards to assign certain patterns to teams but Luciq supports only the following wildcard patterns:

{% hint style="success" %}
## **Example**

**\*/src/payments**

**/src/payments/\***
{% endhint %}

{% hint style="danger" %}
### Examples of unsupported wildcard patterns

* _**/src/\***_**/payment/**
* _\***.rb**_
* **src/**\*\***/test/**
* **src/action**\*\* /test
{% endhint %}

### Team Selection Logic

If multiple teams are assigned to the same path, only the first team on the line will be used.

Example:

```
/src/payment/file1.txt @teamA @teamB
```

@teamA will be assigned to this path
