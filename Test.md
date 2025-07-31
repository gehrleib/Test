## Story
As a data integrity steward, I want the system to automatically clear irrelevant M&T override data, so that our control records are accurate and free of manual errors.

---

### Description

#### Problem Statement:
The `A2A - M&T - Reset Next Test Year Override` process currently leaves the **Next Control Test Year (Override)** and its associated comments intact even when the **In Scope for M&T** flag is set to `No`. This creates misleading and irrelevant data, which requires manual intervention to correct.

#### Solution:
Modify the `A2A - M&T - Reset Next Test Year Override` process. When the **In Scope for M&T** flag is `No`, the process must also clear the value in the **Next Control Test Year (Override)** field and remove any related comments.

---

### Acceptance Criteria

* **Given** a control record where **In Scope for M&T** is `No`.
* **When** the `A2A - M&T - Reset Next Test Year Override` process is executed.
* **Then** the **Next Control Test Year (Override)** field value must be set to null.
* **And** all comments related to the override must be removed from the control record.
