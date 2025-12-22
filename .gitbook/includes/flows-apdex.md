---
title: Flows Apdex
---

Luciq calculates an Apdex score that reflects the performance of your Flows. An Apdex score ranges between 0 and 1; the higher the value, the better the performance:

* Apdex score ≥ 0.94 equates to **Excellent** performance.
* Apdex score ≥ 0.85 and < 0.94 equates to **Good** performance.
* Apdex score ≥ 0.7 and < 0.85 equates to **Fair** performance.
* Apdex score ≥ 0.5 and < 0.7 equates to **Poor** performance.
* Apdex score < 0.5 is considered **Unacceptable**.

The following color-code criteria are also applied:

<figure><img src="https://files.readme.io/4759f658f2055665c9eed93fbd1bc9caedfb037ed6df00e89abf08daddbc3122-flows-apdex-1.png" alt=""><figcaption></figcaption></figure>

## How is the Flow Apdex calculated?

There are two factors that affect the apdex of a Flow: flow latency and drop-offs.

### Flow Latency

When a completed occurrence of a Flow is collected from the SDK, **it is flagged based on the target duration (T) for that Flow**. A Flow occurrence is considered:

* **Satisfying**: if its duration ≤ T
* **Tolerable**: if its duration > T and ≤ 4T
* **Frustrating**: if its duration > 4T

### Drop-Offs

If the occurrences were a drop-off (and therefore don’t have a completion time), we then consider the reason for the drop-off. A Flow occurrence is considered:

* **Frustrating**: if the drop-off reason was a Crash, User Termination, Fatal ANR, or Fatal App Hang
* **Neutral**: if the drop-off was due to user abandonment or the flow timing out in the background.

{% hint style="info" %}
📘 Neutral occurrences **don’t affect** the Apdex of a Flow in any way.
{% endhint %}

### Apdex Calculation

The Apdex score for the entire flow is then calculated as follows:

* **Apdex score = (Satisfying occurrences + 0.5\* Tolerable occurrences) / Total occurrences**
  * Where: Total occurrences = Satisfying occurrences + Tolerable occurrences + Frustrating occurrences

For example, if a Flow had 5 satisfying occurrences, 3 tolerable occurrences, 2 frustrating occurrences, and 1 neutral occurrence, we discard the neutral occurrence and calculate the Apdex as follows:

Apdex score = (5 satisfying occurrences + 0.5 \* 3 tolerable occurrences) / 10 total occurrences = 0.65

## How to control a specific Flow's target?

By default, the target for all Flows is set to **0.5 seconds**; however, you can easily change this number from your dashboard by **clicking on the target highlighted next to each Flow or inside the flow details page**.

<figure><img src="https://files.readme.io/3e3bb91659776cc5d05ac698ad6726a2069baf301a6423be794144777610f149-image.png" alt=""><figcaption></figcaption></figure>

<figure><img src="https://files.readme.io/2f9ec1ac1dbca4ab7850d5aebf65d6a74c00c5df6d78a71ec7b76bc0465452fe-image.png" alt=""><figcaption></figcaption></figure>
