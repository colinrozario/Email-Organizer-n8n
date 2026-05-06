# Email Organizer Workflow using n8n

This repository contains an enhanced Email Organizer Workflow built using n8n. The workflow leverages an AI model to intelligently classify incoming emails into specific categories—Promotions, Socials, Personal, and Career—and then performs automated cleanup actions based on the classification.

## Project Files

- `Email Inbox.json`: The n8n workflow configuration file. Import this into your n8n instance to deploy the workflow.
- `README.md`: This documentation file.

## 1. Workflow Overview

The core of this automation is an AI-driven classification system. The workflow is triggered immediately upon the arrival of a new email. It utilizes a Message a Model node for intelligent content analysis and a Switch node to route the email into the appropriate automated action path.

### High-Level Workflow Steps:

- **Gmail Trigger** – Detects new emails
- **AI Model** – Classifies email content
- **Switch Node** – Routes email based on the assigned category
- **Gmail Actions** – Labels the email, marks it as read, and performs cleanup

## 2. Key Components

The workflow utilizes the following essential n8n nodes for operation:

| Component      | Function |
|----------------|----------|
| Gmail Trigger  | Monitors the connected inbox for new incoming emails |
| Message a Model| Uses an AI model for intelligent email classification |
| Switch Node    | Directs the workflow path based on the output of the AI model |
| Gmail Nodes    | Applies labels (Promotions, Socials, etc.) and performs cleanup actions |

## 3. Updated Workflow Nodes

This section details the sequential nodes configured within the n8n canvas:

- **Gmail Trigger**: Listens for all incoming emails in the primary inbox.
- **Message a Model**: Uses the AI to analyze the email and assign one of the predefined categories.
- **Switch Node**: Routes the workflow into one of the following distinct branches:
  - Promotions
  - Socials
  - Personal
  - Career
- **Gmail Label Nodes**: In each branch, the corresponding label is applied to the email (e.g., the 'Socials' branch applies the "Socials" label).
- **Mark as Read Node**: Marks the email as read after processing.
- **Remove Label Node**: A final cleanup step, potentially removing a default label like "Inbox" if desired, for complete categorization.

## 4. AI Classification Logic

The AI model is the critical component for intelligence within the workflow.

The model is prompted to analyze the following data points from the incoming email to assign a single category:

- Email Subject Line
- Email Sender
- Email Body Content

### Output Categories:

The model is configured to assign one of the following five classification tags:

- Promotions
- Socials
- Personal
- Career
- Misc (For all other uncategorized emails)

## 5. Deployment

To activate the Email Organizer, the user must perform the following steps:

1. Verify the connection credentials for the Gmail service.
2. Ensure the AI Model node is correctly configured and has access to the classification logic.
3. Activate the entire workflow within the n8n application.

### Monitoring

It is essential to monitor initial executions to ensure the AI classification is accurate and the subsequent routing and labeling are working as intended. The execution logs will provide detailed steps for each processed email.