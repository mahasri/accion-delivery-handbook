# Metrics & KPI Definitions

## Development Projects

### Velocity

Velocity variance (SCRUM): Actual Story Points completed over Planned Story Points.

**Benefits:**
- Improve Estimation of team velocity for a sprint.
- Identify areas of improvement that can boost velocity.

### Team Capacity

Team Capacity is the measure of the total amount of work a team can realistically complete during a sprint, based on the availability and productivity of its members. It is typically determined by assessing each team member's available working hours or effort for upcoming sprints and aggregating these to form an overall capacity metric, often expressed as a percentage of total potential output. This metric helps teams plan and balance their workload to ensure that the sprint goals are achievable.

### Burndown

Progress of work completed (Scrum).

Graphical representation of completion of stories & tasks assigned.

**Benefits:**
- Understand estimation and planning efficiency.
- Predict spill over ahead of sprint closure.
- Improvements to effective planning, story writing and story pointing.

### Cycle Time

Time taken to deliver a task or ticket.

Cycle Time (In Days) = All the sprint tasks must qualify DoD within the planned sprint duration.

### Defect Density (QA)

Development Effectiveness (Scrum).

Number of high-severity defects found during QA testing per size (story point) or per # of test cases executed. Can also include weights for each severity level to get more accurate measure.

**Development Effectiveness (Scrum):**
- Understand development quality.
- Identify areas of improvement in scope creation and development effectiveness.

### Defect Density (UAT)

Number of high-severity defects found during UAT testing per size (story point) or per # of test cases executed.

Can also include weights for each severity level of defect identified.

**QA & Development Effectiveness (Scrum):**
- Understand development quality and QA effectiveness.
- Identify areas of improvement in scope creation, QA efficiency and development quality.

### Escaped Defects (P1, P2)

Number of faults detected (Severity 1, Severity 2) in production during the next two weeks after deployment into production.

**Application Quality - Production Fault Density (Scrum):**
- Immediate action to be taken, RCA to be developed and mitigation plans incorporated in the development process.

### First-Time Right Ratio

(Total # of deployments - Total # of rollbacks) / Total # of deployments.

**Deployment - First Time Right (Mandatory If we have the release management in our scope):**
- Quality of deliverables and SDLC process.
- Analyze rollbacks to identify areas of improvement during deployment readiness.

### Rework Effort due to Code Churn

Total Hours / Days between "QA Failed" to "Ready for UAT" status.

Hours spent on rework due to bugs introduced in code.

- Developer quality of work.
- Measure of scope & product understanding of the developers.

### Effort Variance

Effort Variance: Difference between the planned outlined effort and the effort required to complete the task(s).

Effort variance = (Actual Effort – Planned Effort)/ Planned Effort x 100.

### Requirement Stability Index

Provides visibility to the magnitude and impact of requirements changes.

RSI = 1- ((Number of changed + Number of deleted + Number of added) / Total number of initial requirements) x100.

### Residual defect density

Overall % of Customer defects across the defects found in the Project-by-Project team.

Residual defect density = (total number of defects found by a customer)/ (Total number of defects including customer-found defects) x 100.

### Defect Removal Efficiency (DRE)

DRE (%) = [Total Defects Found in Testing / (Total Defects Found in Testing + Total Defects Found in Production)] x 100.

- DRE formula acts as a compass in determining and quantifying the quality of your software product.
- This efficiency metric isn't just about numbers; it's about foresight.

### Test Coverage

Test coverage = line of code covered by test*100/total lines of code.

- Test coverage acts as an indirect quality check method as it helps identify a quantitative measure of how much code you cover.
- Test Coverage helps identify gaps in test cases and requirements.

## DORA Metrics

A set of four key metrics that measure the performance of Software Delivery.

- **Deployment frequency:** How often deployments are made.
- **Lead time for changes:** The time between acceptance and deployment.
- **Change failure rate:** The percentage of deployments that cause failures.
- **Mean time to restore service:** How long it takes to recover from a failure.

**Benefits:**
- Measure team performance: DORA metrics help in understanding how well engineering teams are performing.
- Identify improvement areas: They highlight areas that need attention and improvement.
- Set goals for SLAs: They help in setting realistic service-level agreements (SLAs).
- Establish SDLC baselines: They provide benchmarks for the software development lifecycle (SDLC).
- Data-driven decisions: They enable making informed decisions to improve processes, teams, and applications.

## Support Projects

Note: All metrics data is to be derived from the PM tool being used.

### Cycle Time

Difference between the Planned date and Actual date of an assigned task.

**Cycle Time (Kanban):**
- Understand time taken to complete repeated tasks.
- Identify improvement areas like automation.

### Avg Response Time

Average response time per customer ticket raised.

**Performance of Support Team:**
- Team understanding of the SOPs.
- Effective communication and Collaboration channels.

### Avg Resolution time

Average Resolution time per customer ticket assigned.

**Performance of Support Team:**
- Troubleshooting efficiency.
- Helps in improving troubleshooting processes, documentation, team training and collaboration.

### Mean Time to Resolution (MTTR)

The average amount of time it takes to respond to or resolve an incident.

- MTTR can show how quickly your team is able to respond to or resolve issues as they arise.

### Service Legal Agreement (SLA)

SLA=No. of Incidents Resolved/Total No of Incidents.

- The SLA outlines an agreement between you (the provider) and your clients regarding metrics such as uptime and/or responsiveness.
- The SLA should be constantly monitored and updated to reflect the current state of your service accurately.

---

*Previous: [Agile Methodologies ←](../agile-methodologies/)* | *Next: [Delivery Governance →](../delivery-governance/)*
