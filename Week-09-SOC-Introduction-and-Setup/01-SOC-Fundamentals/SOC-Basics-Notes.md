# SOC Fundamentals

## People, Process & Security Technologies

**DG Interns Hub**\
Cybersecurity Internship \| Week 09\
*A Technical Learning Guide*

------------------------------------------------------------------------

## 1. Introduction to the SOC

A **Security Operations Center (SOC)** is a centralized function that
combines people, defined processes, and supporting technology to
continuously monitor an organization's networks, systems, and
applications. Its purpose is to detect, investigate, and respond to
cybersecurity threats. A SOC turns raw security data into informed
decisions.

### Why Organizations Need a SOC

-   Cyberattacks can occur at any time, so monitoring must be
    continuous.
-   Modern environments generate more logs and alerts than people can
    review manually.
-   Early detection reduces the time an attacker remains unnoticed and
    limits damage.
-   A consistent, documented response reduces confusion and supports
    compliance.

### Core Objectives

-   Detect threats quickly and accurately.
-   Reduce the time taken to detect and respond.
-   Contain incidents and limit business impact.
-   Preserve evidence and maintain clear records.
-   Learn from incidents to strengthen defenses.

## 2. Major SOC Responsibilities

  -----------------------------------------------------------------------
  Responsibility                      Description
  ----------------------------------- -----------------------------------
  **Continuous monitoring**           Watching dashboards, logs, and
                                      alerts across networks, endpoints,
                                      and cloud services.

  **Threat detection**                Identifying suspicious behavior
                                      through rules, correlation, and
                                      analytics.

  **Alert investigation**             Validating alerts and separating
                                      genuine threats from false
                                      positives.

  **Incident response**               Containing, eradicating, and
                                      recovering from confirmed
                                      incidents.

  **Threat intelligence**             Using knowledge of attacker tactics
                                      and indicators to improve
                                      detection.

  **Reporting & documentation**       Recording findings, actions, and
                                      lessons for stakeholders and
                                      audits.
  -----------------------------------------------------------------------

## 3. SOC Workflow

1.  **Data Collection** --- Logs and traffic are gathered from different
    sources.
2.  **Monitoring & Detection** --- Rules and analytics flag anomalies.
3.  **Alert Triage** --- Alerts are validated and prioritized.
4.  **Investigation** --- Evidence is analyzed to confirm scope.
5.  **Incident Response** --- Containment, eradication, and recovery
    take place.
6.  **Documentation** --- Actions and lessons are recorded.

Lessons learned feed back into detection rules and monitoring.

### Illustrative Scenario: Suspicious Outbound Traffic

A workstation begins making steady connections to an unfamiliar external
IP address at 2 a.m. Firewall and DNS logs reach the SIEM, where a rule
for abnormal outbound volume raises an alert. The analyst checks the
destination against threat intelligence, finds it flagged as suspicious,
and reviews host logs to identify the process responsible. The host is
isolated from the network, case notes are completed, and the detection
rule is refined.

*Illustrative scenario for learning purposes.*

## 4. SOC Analyst Levels

Many SOCs organize analysts into tiers so routine alerts are handled
quickly while complex incidents receive deeper expertise. The **L1 / L2
/ L3** model is common, but titles, boundaries, and team sizes differ
between organizations. Some organizations use fewer tiers, merge roles,
or add specialist teams.

### Three-Level SOC Hierarchy

#### L1 --- Alert Monitoring & Triage

-   Monitors security dashboards.
-   Performs initial alert validation.
-   Identifies false positives.
-   Collects basic evidence.
-   Escalates relevant incidents.

#### L2 --- Incident Investigation & Response

-   Conducts detailed alert investigation.
-   Analyzes logs and network traffic.
-   Correlates events.
-   Assesses incident scope and impact.
-   Supports containment and mitigation.

#### L3 --- Advanced Threat Analysis & Threat Hunting

-   Investigates complex incidents.
-   Performs advanced threat hunting.
-   Analyzes malware and attacker techniques.
-   Conducts root-cause analysis.
-   Develops detections and improves security.

### Escalation Flow

**L1 Triage → L2 Investigation → L3 Deep Analysis**

-   False positives or resolved alerts can be closed with notes.
-   Cases needing deeper analysis move from L1 to L2.
-   Complex or high-impact cases move from L2 to L3.
-   Findings feed new detections and playbooks.

### Responsibilities at a Glance

  -----------------------------------------------------------------------
  Level             Primary Focus     Typical Inputs    Typical Outcome
  ----------------- ----------------- ----------------- -----------------
  **L1**            Monitoring and    Alerts,           Closed as benign
                    triage of         dashboards,       or escalated with
                    incoming alerts   tickets           evidence

  **L2**            Investigation,    Escalated cases,  Confirmed scope
                    correlation, and  logs, network     and impact;
                    response support  traffic           containment
                                                        actions

  **L3**            Advanced          Complex cases,    Root cause, new
                    analysis,         threat            detections,
                    hunting, and      intelligence,     stronger defenses
                    improvement       telemetry         
  -----------------------------------------------------------------------

### Example: An Alert Moving Between Levels

-   **L1:** The SIEM raises an alert for many failed logins to one
    account, followed by a successful login from an unfamiliar IP. L1
    checks whether the activity matches known user behavior, adds
    account details, timestamps, and source IP to the ticket, then
    escalates.
-   **L2:** Reviews authentication and VPN logs, correlates the IP with
    other systems, and finds that the account accessed a file server. L2
    supports containment by disabling the account and forcing a password
    reset.
-   **L3:** Investigates how the credentials were obtained, hunts for
    the same pattern across other accounts, and builds an improved
    detection for repeated failures followed by a login from a new
    location.

*Illustrative scenario. Actual escalation criteria are defined by each
organization's own playbooks.*

## 5. Security Technologies: SIEM, IDS, and IPS

These technologies are often discussed together, but they perform
different functions. IDS and IPS inspect activity for malicious
patterns, while a SIEM combines data from multiple sources to provide a
broader view.

### SIEM --- Security Information and Event Management

-   Centralizes log collection.
-   Correlates and analyzes events.
-   Generates alerts.
-   Supports security monitoring and reporting.

**Examples:** Splunk, IBM QRadar, Microsoft Sentinel, Wazuh.

### IDS --- Intrusion Detection System

-   Monitors network or host activity.
-   Detects suspicious traffic.
-   Generates alerts for analysts.
-   Generally operates passively and does not automatically block
    traffic.

**Example:** Snort in IDS mode.

### IPS --- Intrusion Prevention System

-   Detects threats and actively prevents them.
-   Monitors traffic inline, in the traffic path.
-   Drops malicious packets or blocks connections.
-   Requires careful tuning to avoid blocking legitimate traffic.

**Example:** Suricata in IPS mode.

## 6. SIEM vs IDS vs IPS: Comparison

  -----------------------------------------------------------------------
  Feature           SIEM              IDS               IPS
  ----------------- ----------------- ----------------- -----------------
  **Primary         Centralize,       Detect suspicious Detect and block
  purpose**         correlate, and    activity and      malicious
                    analyze security  alert             activity
                    events                              

  **Data            Logs and events   Network traffic   Live network
  monitored**       from many         or host activity  traffic passing
                    sources,                            through it
                    including IDS and                   
                    IPS                                 

  **Detection       Correlation       Signature- and    Signature- and
  capability**      across sources    anomaly-based     anomaly-based
                    and over time     detection         detection in real
                                                        time

  **Alert           Yes, through      Yes; its primary  Yes, plus a
  generation**      correlation rules output            record of actions
                    and analytics                       taken

  **Automatic       Not by itself;    No; generally     Yes; drops or
  blocking**        response is       passive           blocks traffic
                    through analysts                    
                    or integrations                     

  **Deployment      Agents, syslog,   Out of band using Inline in the
  approach**        and APIs feed a   a TAP/SPAN copy,  traffic path, or
                    central platform  or on a host      host-based
  -----------------------------------------------------------------------

## 7. How SIEM, IDS, and IPS Work Together

1.  **Internet traffic** reaches the protected environment.
2.  **IPS** sits inline and can block malicious traffic before it
    reaches its target.
3.  **IDS** passively examines a copy of traffic (for example, through a
    TAP or SPAN) and raises alerts.
4.  **Protected hosts** generate system and application logs.
5.  **SIEM** collects and correlates IDS alerts, IPS prevention logs,
    and system/application logs.
6.  **SOC analysts** investigate the correlated events and take
    appropriate action.

## 8. Key Takeaways

### SOC = People + Process + Technology

  -----------------------------------------------------------------------
  People                  Process                 Technology
  ----------------------- ----------------------- -----------------------
  L1, L2, and L3 analysts Triage, escalation,     SIEM, IDS, and IPS
                          documentation           

  -----------------------------------------------------------------------

### Essentials at a Glance

  -----------------------------------------------------------------------
  L1                      L2                      L3
  ----------------------- ----------------------- -----------------------
  **Monitor and triage**  **Investigate and       **Advanced analysis and
                          respond**               threat hunting**

  Watches alerts,         Investigates escalated  Handles complex
  validates them, and     cases, correlates       incidents, hunts
  escalates what matters. evidence, and supports  proactively, and
                          containment.            improves detections.
  -----------------------------------------------------------------------

  -----------------------------------------------------------------------
  SIEM                    IDS                     IPS
  ----------------------- ----------------------- -----------------------
  **Collect, correlate,   **Detect and alert**    **Detect and prevent**
  analyze**                                       

  Centralizes logs and    Watches traffic or      Sits inline and blocks
  links events from many  hosts passively and     malicious traffic
  sources into alerts.    notifies analysts.      before it reaches its
                                                  target.
  -----------------------------------------------------------------------

## 9. Conclusion

Effective security monitoring depends on all three pillars working
together. Sensors such as IDS and IPS produce and enforce detections; a
SIEM brings those signals together with logs from across the
environment; and tiered analysts turn them into verified findings and
timely action. Understanding how each component fits makes it easier to
follow an alert from its first signal to a documented resolution---the
foundation of practical security monitoring and incident response.

## 10. Learning Outcomes

After reviewing these fundamentals, the learner can:

-   Understand SOC structure and workflows.
-   Recognize SOC analyst responsibilities.
-   Differentiate SIEM, IDS, and IPS.
-   Build foundational knowledge for practical SOC monitoring.

------------------------------------------------------------------------

*DG Interns Hub \| Cybersecurity Internship \| Week 09*
