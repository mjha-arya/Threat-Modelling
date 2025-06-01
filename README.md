# Threat Modeling Guide  
_Systematic Approach to Identifying and Prioritizing Security Risks_

---

## 📖 Overview  
This repository contains the **“Threat Modeling Notes”**—a concise reference outlining definitions, approaches, methodologies, and step-by-step processes for threat modeling. Use this guide to systematically enumerate potential threats, assess risk, and prioritize mitigations for any application or system.

---

## 📂 Repository Contents  


---

## 📝 What Is Threat Modeling?  

- **Threat Modeling**: A repeatable, holistic methodology for listing all potential ways an application or system can be attacked.  
- **Goal**: Proactively detect how something could be exploited, then prioritize and mitigate those risks before they materialize.

### Key Concepts  

- **Weakness (Bug)**: A software defect.  
- **Vulnerability**: A weakness that can be exploited.  
- **Attack Components**:
  - **Target**: The asset or resource of value.  
  - **Attack Vector**: The path an attacker uses to exploit a vulnerability (e.g., SQL injection through a web form).  
  - **Threat Actor/Source**: The individual, group, or external force carrying out the attack.  
- **Attack Surface**: All points (endpoints, interfaces, services) that an attacker can interact with.  
- **Risk** = **Impact** × **Likelihood**  
  - **Impact**: Negative outcome if the attack succeeds.  
  - **Likelihood**: Probability the threat will occur.

---

## 🎯 Why Perform Threat Modeling?  

- **Proactive Risk Reduction**  
  - Detect bugs early, saving time and resources.  
  - Identify business-critical threats before they become incidents.  
- **Holistic Coverage**  
  - Considers the entire environment—not just isolated components.  
  - Produces a prioritized list of potential threats and risks.  
- **Outputs**  
  - **Threat List & Scenarios**: Concrete ways an adversary might attack.  
  - **Data Flow Diagrams (DFDs)**: Visualize how data moves and where threats arise.  
  - **Security Requirements**: Define “must-have” and “non-requirements” for security controls.

### Who Should Threat Model?  

- Security Architects  
- Developers & Testers  
- Security Professionals  
- Stakeholders involved in design, risk assessment, or governance  

---

## ⏰ When to Perform Threat Modeling  

- **As Early as Possible**  
  - Ideally during the design/requirements phase.  
  - Repeat in each development sprint or major architectural change.  
- **Continuous Process**  
  - Revisit once the application or features are deployed and periodically as threats evolve.

---

## 🔍 Approaches to Threat Modeling  

There are three primary “lenses” to begin enumeration:

1. **Asset (Risk)-Centric**  
   - List critical assets to protect (data stores, servers, credentials).  
   - Draw asset/component diagrams and data flows to see how assets interconnect.  
   - For each asset, identify potential threats.  
   - **Pros**: Focus on business impact; aligns well with audit/risk teams.  
   - **Cons**: Assets don’t always map one-to-one with threats.  

2. **Attacker (Security)-Centric**  
   - Profile likely threat actors (motives, capabilities, opportunity).  
   - Enumerate how each attacker could reach objectives (attack paths).  
   - **Pros**: Makes specific threats visible; simulates realistic attack scenarios.  
   - **Cons**: Can miss technical threats; may be biased by analyst assumptions.

3. **Application-Centric**  
   - Visualize the application’s processes, entities, and data flows (DFDs).  
   - Use a classification model (e.g., STRIDE, OWASP Top 10) to list threats per component.  
   - Rank threats by severity using a risk-rating scheme.  
   - **Pros**: Improves developer/architect understanding; integrates well into SDLC.  
   - **Cons**: Requires thorough documentation and can feel abstract at first.

> **Choosing an Approach** depends on your team’s skillset, the organization’s risk appetite, and the type of application.

---

## 📐 Threat Modeling Methodologies  

### 1. PASTA (Process for Attack Simulation and Threat Analysis)  
- **Type**: Asset-Centric (with threat intelligence integration)  
- **Seven Stages**:  
  1. Define Business Objectives  
  2. Define Technical Scope  
  3. Decompose Application (create DFD)  
  4. Threat Intelligence & Analysis (current threat actor TTPs)  
  5. Identify & Rank Vulnerabilities  
  6. Enumerate Attacks (attack trees mapping assets → vulnerabilities)  
  7. Impact Analysis (risk analysis vs. business tolerance)  
- **Use Case**:  
  - Medium to large, mature organizations with executive buy-in.  
  - Iterative, management-focused output.  
- **Pros**: Strong business integration, tooling available.  
- **Cons**: Time-consuming, verbose, requires specialized skills.

### 2. Microsoft Threat Modeling (STRIDE-Based)  
- **Type**: Application-Centric  
- **STRIDE Categories**:  
  - **S**poofing  
  - **T**ampering  
  - **R**epudiation  
  - **I**nformation Disclosure  
  - **D**enial of Service  
  - **E**levation of Privilege  
- **Process**:  
  1. Identify Assets  
  2. Create Architecture Overview (DFD)  
  3. Decompose Application  
  4. Identify Threats (using STRIDE)  
  5. Document & Rate Threats (DREAD, CVSS, OWASP risk rating)  
- **Pros**: Lightweight, developer-driven, integrates into SDLC.  
- **Cons**: Technical focus only; not a full business-risk view.

### 3. OCTAVE (Operationally Critical Threat, Asset & Vulnerability Evaluation)  
- **Type**: Risk-Centric (organizational level)  
- **Variants**:  
  - **OCTAVE-S**: Simplified for smaller organizations.  
  - **OCTAVE Allegro**: Focus on information assets.  
- **Process**:  
  1. Establish Organizational Drivers  
  2. Asset Profiling  
  3. Identify Threats  
  4. Mitigate Risks  
- **Pros**: Improves risk awareness, flexible, organization-wide view.  
- **Cons**: Paperwork-heavy, complex, resource-intensive.

### 4. Trike  
- **Type**: Asset-Centric (tool + methodology)  
- **Process Phases**:  
  1. **System Analysis**: Describe system and high-level security goals.  
  2. **Security Analysis**: Identify threats, investigate mitigations.  
- **Outputs**:  
  - Requirements Model  
  - Implementation Model  
  - Risk Model  
- **Pros**: Automated threat generation, consistent results.  
- **Cons**: Scalability issues, project appears defunct.

### 5. VAST (Visual, Agile, Simple Threat Modeling)  
- **Type**: Process-Centric (scalable for CI/CD)  
- **Variants**:  
  - Application Threat Model  
  - Operational Threat Model  
- **Process**: Uses process flow diagrams (PFDs) rather than DFDs to illustrate workflows.  
- **Pros**: Scalable, integrates with agile teams.  
- **Cons**: Proprietary methodology, less open than other frameworks.

> **Selecting a Methodology** depends on:  
> - Team size and expertise  
> - Organizational risk posture  
> - Project scope and timeline  

---

## 🔄 Common Threat Modeling Process (Example)  

1. **Set Scope**  
   - Define in-scope vs. out-of-scope assets (applications, data stores, external entities).  

2. **Draw Data Flow Diagram (DFD)**  
   - Identify processes, data flows, data stores, external entities, and trust boundaries.  
   - DFD Elements:  
     - **Process**: Rectangle or circle (application component).  
     - **Data Flow**: Arrow connecting components.  
     - **Data Store**: Two parallel lines (database, file store).  
     - **External Entity**: Square (systems or users outside scope).  
     - **Trust Boundary**: Dashed line separating differing privilege levels.  

3. **Identify Threats**  
   - Use a classification model (e.g., STRIDE, OWASP Top 10, CAPEC) to list threats for each DFD element.  
   - Document for each threat:  
     - **Target**: Asset or component under attack.  
     - **Attack Technique**: How the threat manifests.  
     - **Countermeasure**: Mitigation or control.  
     - **Risk Rating**: DREAD, CVSS, or OWASP risk score.

4. **Rate & Prioritize**  
   - Apply a risk-rating framework:  
     - **DREAD**: Damage potential, Reproducibility, Exploitability, Affected users, Discoverability.  
     - **OWASP Risk Rating**: Considers threat agent factors, vulnerability factors, technical impact, business impact.  
     - **CVSS**: Industry-standard scoring (Base, Temporal, Environmental).  
   - Calculate **Risk** = **Impact** × **Likelihood** and rank accordingly.

5. **Document Security Profile**  
   - Detail how the application handles security-sensitive areas:  
     - Session management  
     - Cryptography  
     - Authentication & authorization  
     - Auditing & logging  

6. **Generate Threat & Attack Trees** (Optional)  
   - Visualize complex attack paths: root goal → sub-goals → leaf nodes (vulnerabilities).  

7. **Review & Iterate**  
   - Revisit threat model after design changes or significant updates.  
   - Validate that mitigations sufficiently reduce risk.  

---

## 📊 Summary of Steps  

1. **Scope Definition**  
   - List assets, components, and boundaries of the system.  
2. **DFD Creation**  
   - Map processes, data flows, stores, and trust boundaries.  
3. **Threat Enumeration**  
   - Apply STRIDE/OWASP/other classification per DFD element.  
4. **Risk Rating**  
   - Use DREAD, CVSS, or OWASP methodologies to score each threat.  
5. **Mitigation Planning**  
   - Identify countermeasures; update design to address high-risk items.  
6. **Documentation**  
   - Record threats, risk scores, mitigations, security profile, and assumptions.  
7. **Iteration & Validation**  
   - Reassess periodically as the system or threat landscape evolves.

---

## 📚 References & Resources  

- **STRIDE Model**:  
  https://docs.microsoft.com/azure/security/develop/threat-modeling-stride  
- **OWASP Top 10**:  
  https://owasp.org/www-project-top-ten/  
- **DREAD Risk Model**:  
  https://owasp.org/www-community/controls/DREAD  
- **CVSS Scoring**:  
  https://www.first.org/cvss/  
- **MITRE ATT&CK & CAPEC**:  
  https://attack.mitre.org/  
  https://capec.mitre.org/  
- **PASTA Framework**:  
  https://www.process.st/pasta-threat-modeling/  
- **OCTAVE**:  
  https://www.cert.org/octave/  
- **Trike**:  
  https://insights.sei.cmu.edu/cert/2012/09/threat-modeling-with-trike.html  
- **VAST**:  
  https://www.vastsecurity.com/  
- **Microsoft Threat Modeling Tool**:  
  https://www.microsoft.com/security/blog/2016/09/01/announcing-the-threat-modeling-tool-preview/  

---

> **Note:** Always update your threat model when new features or threats emerge. A living threat model is crucial for maintaining application security and reducing overall risk.

