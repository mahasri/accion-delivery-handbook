# Requirements Gathering Best Practices

This document aims to provide the best practices in the requirements gathering phase of the Agile Software Development Life Cycle (SDLC) and Stakeholder responsibilities to emphasize iterative development and collaboration practices followed at Accion Labs.

## Roles & Responsibilities

The below table provides actionable responsibilities for each stakeholder during backlog refinement, paired with real-world examples and references to ensure clarity and alignment with industry standards.

### Product Owner (PO)

- Collaborate with Stakeholders, Customers, and end-users to gather functional and non-functional requirements in the form of wireframes, documents and PDFs.

- Create and maintain a prioritized product backlog that captures all identified requirements and ensures it remains up-to-date and reflects changing business priorities or Stakeholder inputs.

- Discuss with Stakeholders (internal/ external) to understand & prioritize product increments based on agreed expectations from the product.

- Facilitate brainstorming sessions, interviews, or workshops to identify pain points, desired features, and system constraints.

- Create Epics and User Stories, break down high-level business objectives into epics, User stories, and detailed acceptance criteria. Example: "As a user, I want to reset my password so that I can regain access to my account."

- Collaborate with System Architects to understand technical feasibility and constraints, validate and refine requirements with the Business Analyst.

- Set realistic expectations about deliverables, timelines, and scope limitations. Set priority for User Stories by soliciting information from the Scrum Team and the Architecture experts to ensure technical feasibility.

- Address blockers or dependencies by coordinating with Architects or external teams. Example: Finalizing API contracts for a dependent feature.

### Business Analyst (BA)

- Work with Stakeholders and Product Owners to gather requirements translating them into backlog items as Epics, User stories, or Tasks.

- Review Customer requirements Wireframes / Documents/PDFs.

- Detailed functional requirements using industry-standard templates (e.g., BRD, FRD). Example: Include wireframes for a feature request involving a complex user interface.

- Conduct User interviews / Surveys and present results to the team. Example: A survey reveals the need for multi-language support for the application.

- Validate and refine user stories to ensure alignment with business goals. Example: Confirm that the "export report" functionality meets client compliance standards.

### Project Manager (PM)

- Review wireframes, clickable mockups and identify issues with requirements. Track the team's progress in gathering and documenting requirements to ensure alignment with the project schedule.

- Define activities, timelines, and allocate resources, assign team members, including Business Analysts to the phase.

- Organize and lead meetings between Stakeholders, Business Analysts, and technical teams to gather requirements.

- Identify and document expected outputs of the requirements phase, such as finalized requirement documents, user stories, or use cases.

- Define, and track milestones for completion of key deliverables, Organize and facilitate backlog refinement sessions weekly. Example: Use a 1-hour session to refine 10 top-priority stories.

- Document dependencies and escalate risks to Stakeholders. Example: Flag a delay in API delivery affecting the current sprint.

- Align Backlog scope with Sprint Capacity. Example: Ensure the team commits to a feasible number of stories during Sprint Planning.

### Architect

- Review and evaluate the requirements gathered by the Product Owner or Business Analyst to ensure technical feasibility.

- Participate in the review process to help understand the project and discover value opportunities for the customer.

- Review user stories for technical feasibility. Highlight technical, infrastructural, or resource constraints that might impact the delivery of requirements. Example: Highlight if the proposed feature increases database load beyond capacity.

- Suggest splitting stories based on architectural complexity. Example: Break "Build Analytics Dashboard" into "Create Data Pipeline" and "Build Frontend Dashboard."

- Ensure non-functional requirements are addressed. Example: Add performance requirements like "API latency should not exceed 300ms under peak load."

### Developer / QA

- Work closely with the Product Owner to understand requirements.

- Coordinate with other team members to ensure seamless integration of features.

- Review, estimate User stories, estimate and plan tasks for each sprint.

- Commit to delivering increments that meet the definition of done (DoD).

- Collaborate intensely, and own responsibility of completing all the tasks in a Sprint.

- Identify and raise potential blockers. Example: Flagging the need for a new library to handle image processing in a story.

- Define QA acceptance criteria. Example: "Login should work across all browsers, including Chrome, Edge, and Firefox."

### Engineering Manager

- Management of requirements throughout the project life cycle (SDLC).

- Validate proposed technical solutions for compatibility with existing systems. Example: Approve integration with the client's internal CRM tool.

- Identify external dependencies early. Example: Notify the team of a third-party API's expected downtime during integration testing.

### End Customer

- Provide feedback on requirements. Example: Request "Download Invoice" functionality based on business operation's needs.

- Highlight any compliance or business-specific constraints. Example: Specify adherence to GDPR regulations for data handling features.

## Best Practices in Requirements Gathering

Here are the **best practices** for the requirements gathering phase in Agile SDLC.

### 1. Continuous Stakeholder Engagement

- Continuously engage stakeholders throughout the project lifecycle to ensure alignment on goals.

- Involve product owners, end-users, and developers early in the process to gather valuable feedback.

- Conduct regular backlog refinement sessions to incorporate evolving needs and priorities.

- Use stakeholder personas and mapping to ensure all key participants are identified and involved.

- Hold iterative discussions to adapt and refine requirements as new insights emerge during sprints.

### 2. Incremental Elicitation of Requirements

- Elicit requirements iteratively, refining them over multiple sprints rather than a single, upfront process.

- Break down high-level features into smaller, manageable user stories that can be developed and delivered in short iterations.

- Use techniques like user story mapping, workshops, and interviews to gather detailed requirements over time.

- Focus on immediate sprint goals while maintaining a flexible backlog for future iterations.

- Encourage stakeholders to prioritize features based on business value and technical feasibility.

### 3. Writing Agile User Stories

- Follow the INVEST criteria (Independent, Negotiable, Valuable, Estimable, Small, Testable) for user stories.

- Use the "As a [user], I want [feature] so that [benefit]" format for clear, actionable stories.

- Include acceptance criteria that define what "done" means for each story.

- Keep stories small enough to be completed within a single sprint.

- Regularly review and refine stories based on team feedback and stakeholder input.

---

*[Back to Best Practices & Guidelines](index.md)*
