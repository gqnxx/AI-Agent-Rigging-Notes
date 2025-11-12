
# Day 2: Tool Rigging & Human-in-the-Loop (HITL)

## Day's Goal

Today was all about giving the Agent new "hands" and a robust "employment contract" so it knows how to act and communicate with the outside world. The most critical part: securing dangerous actions with **Human Approval** to prevent self-inflicted disasters.

## Key Technical Takeaways (Engineering and Hardening)

### 1. Custom Tool Implementation

* **Focus:** We converted simple Python functions (like currency conversion and fee calculation) into **real tools** the Agent could understand and invoke.
* **The Rigging:** We used explicit **Docstrings** and function annotations—the Agent reads these descriptions to decide when and how to call the function.

### 2. Operational Security (Human-in-the-Loop) 🛡️

* **The Problem We Solved:** We don't trust an autonomous LLM to process a huge shipment order or delete critical data automatically.
* **The Solution (HITL):** We implemented **Long-Running Operations**. This feature forces the Agent to initiate a **temporary pause (WAIT state)** and wait for a human decision (`APPROVE` or `REJECT`) before proceeding with a sensitive action.
* **The Security Win:** This is the most effective **security control** against rogue agents or **Prompt Injection** attacks that attempt to seize control and execute dangerous commands. It keeps the human in the driver's seat for critical decisions.

### 3. Communication via MCP

* **Focus:** We used the **Model Context Protocol (MCP)** to allow the Agent to communicate with external systems.
* **The Contract:** MCP defines the rules and structure for tool access and data exchange. Any flaw in the MCP implementation could create a vulnerability for malicious external systems to exploit or for the Agent to access unauthorized resources.

## Practical Accomplishments

* **Codelab Day 2a:** Successfully built a Currency Converter Agent that delegated complex calculations to a specialized **Sub-Agent**.
* **Codelab Day 2b:** Implemented and tested **Human-in-the-Loop (HITL)** scenarios, demonstrating successful pausing and continuation after user approval.

---

## Next Steps

* Moving to **Day 3: Quality and Reliability**. We need to figure out how to write harsh tests for these Agents and implement **Agent Ops** principles (monitoring and tracing).
* *Detailed notes and analytic dumps are stored in `Notes/Day_2_Notes.md`.*
