# Learning Management RoadMap AI Agent

## Overview
The **Learning Management RoadMap AI Agent** is an n8n workflow that automates the creation of personalized learning roadmaps from form submissions. It captures user input, stores the submitted data, routes it through rule-based logic, processes it with an AI Agent powered by the **Google Gemini Chat Model**, and updates the final record automatically.

This workflow is useful for generating structured learning plans based on user needs, goals, or skill levels.

---

## Features
- Accepts user input through a form submission
- Saves submitted data into a datastore
- Uses rule-based routing with a **Switch** node
- Processes inputs with an **AI Agent**
- Powered by **Google Gemini Chat Model**
- Updates records automatically with generated roadmap content

---

## Workflow Steps

### 1. Form Submission
**Node:** `On form submission`

The workflow starts when a user submits a form.

- **Trigger Type:** Form-based
- **Purpose:** Collect learner input such as goals, interests, or skill requirements

### 2. Save Data
**Node:** `Save Data`  
**Operation:** `create: record`

This step stores the submitted form data into the connected datastore.

- **Purpose:** Persist submitted information for future use
- **Action:** Create a new record

### 3. Rule-Based Routing
**Node:** `Switch`  
**Mode:** `Rules`

The saved data is evaluated against configured routing rules. Based on the matching rule, the input is passed to the next processing stage.

- **Purpose:** Direct data flow based on conditions or categories
- **Output:** Routed branch to AI processing

### 4. AI Processing
**Node:** `AI Agent`

The AI Agent receives the routed input and generates a learning roadmap or structured response.

- **Purpose:** Create personalized learning guidance
- **Model Connection:** Google Gemini Chat Model

### 5. Chat Model
**Node:** `Google Gemini Chat Model`

This node provides the language model used by the AI Agent for generating intelligent roadmap outputs.

- **Purpose:** Power AI-driven content generation
- **Integration:** Connected directly to the AI Agent

### 6. Update Record
**Node:** `Update record`  
**Operation:** `update: record`

After the AI Agent generates the roadmap, the workflow updates the existing datastore record with the AI-produced result.

- **Purpose:** Save the final roadmap into the system
- **Action:** Update existing record

---

## End-to-End Flow

```text
On form submission
  → Save Data
  → Switch
  → AI Agent
    → Google Gemini Chat Model
  → Update record
