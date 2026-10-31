*Intuz — Your automation partner, one workflow at a time.*

<p align="center">
  <picture>
    <img alt="Banner Image" src="https://github.com/user-attachments/assets/210f97fc-0fce-404a-b647-7dfe1302cd37" />
  </picture>
</p>

[Intuz](https://www.intuz.com) helps organizations orchestrate AI, automation, and enterprise systems through scalable workflows. Our repository showcases proven implementations across healthcare, operations, customer support, document processing, sales, and back-office functions, enabling teams to accelerate automation initiatives without starting from scratch.

[N8N Creator](https://n8n.io/creators/intuz/) · [AI Agent Development Company](https://www.intuz.com/ai-agents-for-business-automation/) · [n8n Workflow Automation](https://www.intuz.com/workflow-automation-services/) · [For Custom Workflow Automation](https://www.intuz.com/get-started/)

# Create and approve Xero invoices from Pipedrive Closed Won deals with Slack

## Quick overview

This workflow triggers when a Pipedrive deal is moved into the Closed Won stage, creates a matching draft invoice in Xero, and posts it to Slack for approval before authorising and emailing the invoice to the customer.

## How it works

1. Triggers when a deal changes in Pipedrive and continues only when the deal newly enters the configured Closed Won stage.
2. Fetches the deal’s person details from Pipedrive and prepares the contact name and email for invoicing.
3. Searches Xero for an existing contact by email (or by name if email is missing) and creates a new Xero contact if none is found.
4. Pulls the deal’s products from Pipedrive, builds Xero invoice line items (or falls back to the deal title/value), and creates an ACCREC draft invoice in Xero with calculated due date and configured currency.
5. Sends the draft invoice details to a Slack channel and waits for an Approve & Send or Reject decision.
6. If approved, updates the invoice in Xero to AUTHORISED and emails it via Xero when an email address is available, then posts a confirmation to Slack.
7. If rejected, leaves the invoice as a draft in Xero and posts a rejection notice to Slack.

## Setup

1. Connect your Pipedrive credentials and ensure the Pipedrive deal-change trigger webhook is registered for your Pipedrive account.
2. Connect your Xero OAuth2 credentials, set your Xero tenant ID (Xero-tenant-id), and confirm your organisation supports the configured invoice currency.
3. Connect your Slack OAuth2 credentials and set the target finance channel for the approval and notification messages.
4. Update the workflow configuration values (Closed Won stage ID, sales account code, tax type, invoice currency, and payment terms days) to match your Pipedrive pipeline and Xero chart of accounts.
5. Ensure Pipedrive deals have an associated person and email address if you want invoices to be emailed automatically from Xero.

## Requirements

- Pipedrive API credential + trigger Action change / Entity deal
- Xero OAuth2 (contacts + invoices); org must be subscribed to the invoice currency (this tenant: INR)
- Slack OAuth2 with permission to post + send-and-wait in the finance channel
- Closed Won mapped to the correct stage_id (here: 84)
- Client person email in Pipedrive for the auto-email step
- Valid Xero sales account code + tax type for your org
- After any edit: click Publish so the live version matches the draft

## FAQ

**What triggers this workflow?**  
The workflow triggers when a Pipedrive deal is moved into the configured Closed Won stage.

**How does the workflow handle invoice approval?**  
It posts the draft invoice details to a Slack channel and waits for an Approve & Send or Reject decision before authorising and emailing the invoice.

**What integrations are required for this workflow?**  
Pipedrive API credentials, Xero OAuth2 credentials with invoice currency support, and Slack OAuth2 credentials with posting permissions are required.

## Related n8n templates from Intuz

- [Integrate Bitcoin in your Application seamlessly with ready made API](https://github.com/Intuz-production/bitcoinJs-API)
- [An n8n workflow that automates closing Jira support tickets by sending customer auto-replies and CSAT requests via WhatsApp or Gmail, saving responses to Jira, and optionally logging notes in HubSpot.](https://github.com/Intuz-production/Automate-Support-CSAT)
- [Turn confirmed Airtable sales orders into QuickBooks invoices — find or create the customer, generate the invoice, and write the Invoice ID back to Airtable.](https://github.com/Intuz-production/Airtable-to-QuickBooks-invoice-automation)

[See all of Intuz's free n8n templates](https://www.intuz.com/n8n-workflow-automation-templates/)

## Connect with us

Intuz is a USA-based AI & workflow automation company with 16+ years of experience building custom AI-enabled workflow automations for SMBs and Enterprises, specializing in agentic AI, LLM integrations, and CRM/ERP sync across Healthcare, FinTech, eCommerce, Manufacturing, and Real Estate.

* **Website:** [https://www.intuz.com](https://www.intuz.com)
* **Email:** [getstarted@intuz.com](mailto:getstarted@intuz.com)
* **LinkedIn:** https://www.linkedin.com/company/intuz/
* **Get Started:** https://n8n.partnerlinks.io/intuz

## For Custom Workflow Automation

[Click here - Get Started](https://www.intuz.com/get-started/)
