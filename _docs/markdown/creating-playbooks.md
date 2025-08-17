
---
title: "Playbooks"
weight: 2
---
![Playbooks](https://github.com/w-hudson/docs/blob/d3f082cec0e85301dd8fd3a71bd8f1f1d96ceb3a/img/placeholder.png)

Playbooks are used to route events that do not require direct investigation and escalation, but should still be logged and seen by your Organization. Playbooks allow for automatic actions to be taken on an event, such as adding comments, escalating the Alert to an individual or Notification Group, and setting a schedule for when the Playbook is active. This allows you to maintain visibility into the traffic in your environment while reducing the number of Alerts that require investigation.

Much like [Filters](placeholderlink), Playbooks use key/value pairs from security events to identify known good behavior and automatically resolve future security events that match the configured logic.

### Create a new Playbook

1. Open the Alert and click **Create Playbook**.
![Create Playbook](https://github.com/w-hudson/docs/blob/d3f082cec0e85301dd8fd3a71bd8f1f1d96ceb3a/img/placeholder.png)
2. Type a name for the new Playbook.
3. Ensure that the **Product**, **Organization**, and **Event Type** are correct.
![Create Playbook](https://github.com/w-hudson/docs/blob/d3f082cec0e85301dd8fd3a71bd8f1f1d96ceb3a/img/placeholder.png)
    - The Organization field defaults to the Organization where the trigger event originated. For an Organization with multiple child Organizations, you can select a specific child Organization or the top-level parent Organization to apply it to all child Organizations.
    - The default event Tier for Playbooks is **Tier 2** (Observations). This event type will not generate an Alert, but may be useful for additional investigative context for other Alerts. You can also select **Tier 3** (Safe) to whitelist an event or **Tier 4** (Discard) to have the platform discard activity that matches your Playbook. For additional information on the event Tiers and their uses, see [Event Tiers](placeholderlink).
   
4. Configure the details you want to use for the Playbook logic:
![Mandatory and Optional Fields](https://github.com/w-hudson/docs/blob/d3f082cec0e85301dd8fd3a71bd8f1f1d96ceb3a/img/placeholder.png)
    - For the **Mandatory Fields**, select key/value pairs from the details of the Alert that match the criteria you want the Playbook to evaluate. 
    You can add multiple fields to ensure that only known safe events match the Playbook; the more specific your criteria, the less likely you are to miscategorize an event. All Mandatory Fields must match the event for the Playbook to apply.
    - **Optional Fields** can be useful to tune the logic of your Playbook or add qualifying values. Multiple Optional Fields act with a **Match Any** operator - if any individual Optional Field matches, then the Playbook is applied. 
5. Configure the **Response Actions**.
![Response Actions](https://github.com/w-hudson/docs/blob/d3f082cec0e85301dd8fd3a71bd8f1f1d96ceb3a/img/placeholder.png)
   - **Event Comments** allows you to add predefined text to the Comments section of any Alert that matches the Playbook. You can insert variables for any of the key/value pairs in the event using the syntax **{{Key Name}}**. Example: **The {{Process Name}} performed {{IOC Query String}}** would show the name of the process and the action that was observed.
   - **Event Hints** are additional pieces of informational text that are displayed in the TAPs section of the event with a question mark (**?**) icon. An example use for an Event Hint would be to recommend other resources or context to assist in investigation of the Alert.
   - **Escalation Paths** allows you to specify a user or Notification Group you want to receive a Notification about any event that matches the Playbook logic.
6. Configure the **Active During** settings. This allows you to specify the schedule for when a Playbook is active. This is useful when you have teams on different schedules. You must create a separate Playbook for each schedule. You can also use the **Start Date** and **End Date** fields so that a Playbook is only active during a specific date range.
![Active During](https://github.com/w-hudson/docs/blob/d3f082cec0e85301dd8fd3a71bd8f1f1d96ceb3a/img/placeholder.png)
4. If the Key/Value pairs in the security event do not provide enough context to safely match the event, you can use **Advanced Filters** to collect additional validation data from your available Threat Analytics Plugins (TAPs). This is also referred to as using a  **Multi-Stage Filter** (MSF). 
![Advanced Filters](https://github.com/w-hudson/docs/blob/d3f082cec0e85301dd8fd3a71bd8f1f1d96ceb3a/img/placeholder.png)
    MSFs use Mandatory and Optional fields for the key/value pairs returned by the TAP. Because some TAPs return multiple pages of data, Advanced Filters can use the **Match Any** or **Match All** operators for the returned TAP data.    
![Advanced Filter Logic](placeholder.png)
    After you have built the MSF logic, click  **Preview TAP** in the top right. If the Advanced Filter logic matches, a green checkmark will appear. If it fails, a red x will appear. When you receive a successful result, click **Add TAP** to add the TAP to your Advanced Filter. 
    
5. Add Comments to describe the reason you created the Filter and any additional information.
6. Click **Validate** to see a list of all current Alerts that would be affected by your new Playbook and modify the logic as necessary so that only the corresponding Alerts are filtered.
7. When you are satisfied that the filter will only affect expected events, click **Save**. The Playbook must be reviewed by a Superuser before it becomes active.

### Editing a Playbook
If you need to modify a Playbook, you can edit its settings under Orchestration.
1. Select **Orchestration** from the left side navigation, then click **Playbook** at the top of the page.
2. Open the Playbook and make any necessary changes.
3. Add Comments to note any changes.
4. Click **Validate** at the bottom of the screen to test your changes.
5. Click **Save** at the bottom of the screen. 

### Reviewing and Activating a Filter
Before a new or modified Playbook can become active, it must be reviewed by a Superuser.
1. Select **Orchestration** from the left side navigation, then click **Playbook** at the top of the page.
2. Scroll, search, or use the drop-down lists to locate the Playbook.
3. Click **Assign to me** to start the review.
4. Check the details and matching logic, then click **Validate** to ensure that only the expected events are affected by the Playbook.
   - If the Playbook does not function as expected, make any necessary changes, save the changes, and perform the **Validate** operation again.
5. Add Comments to note any changes you make to the Filter.
6. When you are satisfied that the Playbook is configured correctly, click **Activate**.
