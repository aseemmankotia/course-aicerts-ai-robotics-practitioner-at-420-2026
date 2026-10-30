## Chapter 9: Robotic Process Automation (RPA) — Practice Questions

**Q1.** A company needs to extract data from unstructured scanned invoices and enter it into their ERP system. Which approach BEST meets this requirement?

A) A pure RPA bot using screen scraping only
B) Intelligent automation combining AI/OCR document extraction with an RPA bot for data entry
C) A physical robot arm equipped with cameras
D) A fully manual data entry team

<details>
<summary>Answer</summary>

**Correct: B**

Unstructured scanned documents require AI (OCR/NLP) to extract data; RPA then handles the repetitive digital entry step. This combination is intelligent automation.

**Why the others are wrong:**
- Pure RPA/screen scraping alone cannot reliably interpret unstructured scanned content without AI.
- A physical robot is irrelevant — the task is entirely digital, not physical.
- Manual entry is not automation and defeats the purpose of the solution.

> ⚠️ Frequently missed on the exam — read the options carefully.

</details>

---

**Q2.** An enterprise wants a bot to run automatically every night to reconcile financial records with no human present. Which type of RPA bot should be deployed?

A) Attended bot
B) Unattended bot
C) Physical robot
D) Chatbot

<details>
<summary>Answer</summary>

**Correct: B**

Unattended bots run on a schedule or trigger without human presence, making them ideal for back-office batch processes like nightly reconciliation.

**Why the others are wrong:**
- Attended bots require a human to trigger them during a live desktop session.
- Physical robots perform physical-world tasks, not digital reconciliation.
- Chatbots handle conversational interactions, not back-office data processing.

> ⚠️ Frequently missed on the exam — read the options carefully.

</details>

---

**Q3.** A help desk agent needs a bot that activates on-demand on their desktop to pull up customer records during a live call. Which bot type fits this scenario?

A) Unattended bot
B) Physical cobot
C) Fully autonomous AI agent
D) Attended bot

<details>
<summary>Answer</summary>

**Correct: D**

Attended bots are triggered by a human during a live task and run on the user's own desktop, ideal for front-office real-time assistance.

**Why the others are wrong:**
- Unattended bots run without human presence, unsuitable for a live-call assist scenario.
- A physical cobot is a hardware device, not relevant to a digital record lookup.
- A fully autonomous AI agent is a different concept and not the standard RPA term for this use case.

</details>

---

**Q4.** A process requires navigating a legacy application's GUI with no available API, clicking buttons, and reading screen text to copy data into a spreadsheet. Which automation technology is MOST appropriate?

A) RPA software bot
B) Physical robotic arm
C) Custom API integration
D) Machine learning model

<details>
<summary>Answer</summary>

**Correct: A**

RPA is purpose-built for UI-level automation of legacy applications with no API, mimicking human clicks and reads.

**Why the others are wrong:**
- The task is entirely digital; a physical robot has no role here.
- No API exists, so custom API integration is not possible.
- An ML model does not perform UI actions by itself; it would need to be paired with RPA.

</details>

---

**Q5.** A manufacturer needs a system to physically pick parts off a conveyor belt and place them into boxes. Which automation technology should be used instead of RPA?

A) RPA unattended bot
B) Attended RPA bot
C) Physical robot (e.g., robotic arm)
D) RPA combined with a chatbot

<details>
<summary>Answer</summary>

**Correct: C**

Physical manipulation of objects requires physical robotics; RPA only automates software/digital tasks, never physical movement.

**Why the others are wrong:**
- Unattended RPA bots operate on software/UI, not physical objects.
- Attended RPA bots also only operate within digital applications.
- RPA plus a chatbot is still purely a digital/software solution, not physical manipulation.

> ⚠️ Frequently missed on the exam — read the options carefully.

</details>

---

**Q6.** A bot's automated process starts failing frequently because the target application's UI layout was updated. What is this RPA limitation called, and what governance practice mitigates it?

A) UI brittleness; mitigated by proactive change management and bot monitoring/maintenance
B) Bot drift; mitigated by hardcoding credentials
C) Model drift; mitigated by retraining the ML model
D) Scalability limit; mitigated by purchasing more bot licenses

<details>
<summary>Answer</summary>

**Correct: A**

UI brittleness is a core, well-recognized RPA limitation; it is mitigated through governance practices such as change management, version control, and proactive monitoring of bot health.

**Why the others are wrong:**
- 'Bot drift' is not a standard term, and hardcoding credentials is an unrelated and poor security practice.
- Model drift applies to ML model performance degradation, not UI-dependent RPA automation.
- Adding more licenses does not fix a broken UI selector or reference.

> ⚠️ Frequently missed on the exam — read the options carefully.

</details>

---

**Q7.** In an RPA bot lifecycle management program, what is the PRIMARY purpose of maintaining a centralized governance framework (e.g., a Center of Excellence)?

A) To eliminate the need for business process documentation
B) To replace all human IT staff with bots
C) To standardize bot development, security, deployment, monitoring, and decommissioning across the organization
D) To guarantee bots never require maintenance

<details>
<summary>Answer</summary>

**Correct: C**

A governance framework/CoE standardizes practices across the full bot lifecycle for consistency, security, and scalability.

**Why the others are wrong:**
- Documentation remains essential regardless of governance.
- Governance does not aim to eliminate human IT roles.
- Bots still require ongoing maintenance, especially due to UI brittleness.

</details>

---

**Q8.** Which statement BEST describes the core distinction between RPA and physical robotics?

A) RPA requires AI while physical robotics does not
B) RPA is always unattended, while physical robots are always attended
C) RPA and physical robotics are interchangeable terms for the same technology
D) RPA automates digital/software-based tasks by interacting with applications and UIs, while physical robotics automates tasks involving manipulation of the physical world

<details>
<summary>Answer</summary>

**Correct: D**

This is the exam's heavily tested core distinction: RPA is the 'digital robot' operating purely in software, while physical robotics manipulates real-world objects.

**Why the others are wrong:**
- RPA does not require AI — it can be combined with AI but functions without it; physical robots may or may not use AI as well.
- Attended/unattended is RPA-specific terminology and does not describe physical robots.
- They are distinct technology categories solving different kinds of problems.

> ⚠️ Frequently missed on the exam — read the options carefully.

</details>

---

