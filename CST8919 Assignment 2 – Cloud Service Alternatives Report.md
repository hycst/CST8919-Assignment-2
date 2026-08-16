#### CST8919 – DevOps Security and Compliance

#### Assignment 2 – Cloud Service Alternatives Report

#### Azure vs. AWS vs. Google Cloud Security Services

#### Introduction

From the couse CST8919, I leaned Cloud providers offer many similar services for identity management, monitoring, governance, security posture management, and threat detection. However, the services are not always direct one-to-one replacements. Microsoft Azure, Amazon Web Services (AWS), and Google Cloud Platform (GCP) use different architectures and sometimes divide the same capability among several products.

This report compares five important Microsoft Azure security and compliance services studied in CST8919 with their closest AWS and Google Cloud alternatives. The comparison focuses on core features, security and compliance, pricing models, and integration with DevSecOps practices.

The five Azure services covered are:

- Microsoft Entra ID (formerly Azure Active Directory)
- Azure Monitor and Log Analytics
- Azure Policy
- Microsoft Defender for Cloud
- Microsoft Sentinel

---

#### 1. Quick Comparison

| Security Area | Microsoft Azure | AWS | Google Cloud |
|---|---|---|---|
| Identity, IAM and SSO | Microsoft Entra ID | AWS IAM Identity Center + AWS IAM | Cloud Identity + Cloud IAM |
| Monitoring and Logging | Azure Monitor + Log Analytics | Amazon CloudWatch | Cloud Monitoring + Cloud Logging |
| Policy and Governance | Azure Policy | AWS Config + Service Control Policies | Organization Policy Service |
| Cloud Security Posture | Microsoft Defender for Cloud | AWS Security Hub | Security Command Center |
| SIEM / SOAR | Microsoft Sentinel | AWS Security Hub + Amazon Security Lake | Google Security Operations |

Although these services provide similar capabilities, they are not always exact equivalents. For example, AWS divides some Microsoft Sentinel-like capabilities among Security Hub, Security Lake, CloudWatch, and other security services rather than providing exactly the same architecture as Microsoft Sentinel.

---

#### 2. Microsoft Entra ID vs. AWS IAM Identity Center vs. Google Cloud Identity

#### Overview

#### Microsoft Azure – Microsoft Entra ID

Microsoft Entra ID, formerly Azure Active Directory, is Microsoft's cloud identity and access management service. It manages users, groups, applications, authentication, authorization, and access to Azure and other applications.

It is heavily used for Single Sign-On (SSO), Multi-Factor Authentication (MFA), Conditional Access, identity federation, and Role-Based Access Control (RBAC).

#### AWS – AWS IAM Identity Center and AWS IAM

AWS divides identity management between two closely related services.

**AWS IAM Identity Center** focuses primarily on workforce identity and centralized Single Sign-On across AWS accounts and applications. **AWS Identity and Access Management (IAM)** controls access to AWS resources through users, roles, permissions, and policies.

IAM Identity Center can connect to an existing identity provider and provides centralized access to multiple AWS accounts and applications.

#### Google Cloud – Cloud Identity and Cloud IAM

Google Cloud also divides identity management into multiple services.

**Cloud Identity** manages users, groups, devices, authentication, and organizational identities. **Cloud IAM** determines which identities are allowed to access specific Google Cloud resources.

Together, they provide functionality similar to Microsoft Entra ID.

#### Core Features

| Feature | Microsoft Entra ID | AWS IAM Identity Center / IAM | Google Cloud Identity / IAM |
|---|---|---|---|
| User and group management | Yes | Yes | Yes |
| Single Sign-On | Yes | Yes | Yes |
| Multi-Factor Authentication | Yes | Yes | Yes |
| Role-based access | Azure RBAC | IAM roles and policies | IAM roles |
| Federation | SAML, OAuth 2.0, OIDC | SAML and external identity providers | SAML, OIDC and federation |
| Conditional access | Strong native support | Available through IAM and related controls | Context-aware and IAM controls |
| Multiple cloud account management | Azure tenants/subscriptions | AWS Organizations + Identity Center | Organizations/folders/projects |

#### Security and Compliance

All three providers support enterprise security capabilities such as MFA, least privilege, federation, centralized access management, auditing, and role-based permissions.

They also operate under major cloud compliance programs. Microsoft, AWS, and Google maintain extensive compliance programs covering standards such as ISO 27001, SOC reporting, PCI DSS and government-related frameworks, although the exact scope depends on the service, region, configuration, and cloud offering.

A major security principle for all three platforms is **least privilege**. Users should receive only the permissions required to perform their responsibilities.

#### Pricing Model

Microsoft Entra ID includes basic capabilities with Microsoft cloud services, while advanced identity protection and Conditional Access capabilities generally depend on premium licensing.

AWS IAM and IAM Identity Center provide many identity-management capabilities without a separate service charge, although supporting AWS services can create additional costs.

Google Cloud Identity provides both free and premium editions. Google currently provides a free Cloud Identity edition, while Cloud Identity Premium is offered using per-user licensing.

#### DevSecOps Integration

Identity management is important to DevSecOps because CI/CD pipelines should not contain permanent administrator usernames and passwords.

Microsoft Entra ID can authenticate Azure DevOps, GitHub Actions, applications, service principals, and managed identities.

AWS IAM supports IAM roles and temporary credentials for deployment pipelines.

Google Cloud IAM supports service accounts and workload identity mechanisms.

These approaches allow automation systems to follow least-privilege principles and reduce the use of long-lived credentials.

#### Analysis

Microsoft Entra ID has particularly strong integration with Microsoft 365 and the wider Microsoft ecosystem. AWS IAM is deeply integrated with AWS services and provides highly detailed policy-based permissions. Google Cloud IAM also provides centralized access control with a strong organization-project-resource hierarchy.

For organizations already using Microsoft 365 extensively, Entra ID may provide the most natural identity platform. Organizations primarily operating AWS workloads may prefer IAM Identity Center and IAM, while Google-focused organizations can use Cloud Identity and IAM.

---

#### 3. Azure Monitor and Log Analytics vs. Amazon CloudWatch vs. Google Cloud Operations

#### Overview

#### Microsoft Azure – Azure Monitor and Log Analytics

Azure Monitor collects metrics, logs, application telemetry, and other operational information from Azure resources.

Log Analytics is used to query and analyze logs stored in Azure Monitor Log Analytics workspaces. Users can investigate logs using **Kusto Query Language (KQL)**.

For example, security teams can examine failed Microsoft Entra ID sign-in attempts using SigninLogs and investigate suspicious authentication activity.

#### AWS – Amazon CloudWatch

Amazon CloudWatch is AWS's primary monitoring and observability platform.

CloudWatch collects metrics, logs, application telemetry, and events from AWS resources and applications. It provides dashboards, alarms, log analysis, and monitoring capabilities.

CloudWatch can collect information from AWS services, custom applications, and third-party sources.

#### Google Cloud – Cloud Monitoring and Cloud Logging

Google separates monitoring and logging into two closely connected services.

**Cloud Monitoring** collects metrics and supports dashboards, alerts, and performance monitoring.

**Cloud Logging** collects, stores, searches, and analyzes logs from Google Cloud resources, applications, and other systems.

Together they provide functionality comparable to Azure Monitor and Log Analytics.

##### Core Features

| Feature | Azure Monitor | Amazon CloudWatch | Google Cloud Operations |
|---|---|---|---|
| Infrastructure metrics | Yes | Yes | Yes |
| Centralized logging | Log Analytics | CloudWatch Logs | Cloud Logging |
| Dashboards | Yes | Yes | Yes |
| Alerts | Yes | Yes | Yes |
| Log queries | KQL | CloudWatch Logs queries | Logs Explorer queries |
| Application monitoring | Application Insights | CloudWatch/APM integrations | Cloud Trace/Monitoring |
| Automation integration | Yes | Yes | Yes |

#### Security and Compliance

Monitoring services support security investigations by maintaining logs of application and infrastructure activity.

For example, logs can help security teams identify:

- Multiple failed login attempts
- Unexpected administrative activity
- Resource configuration changes
- Application failures
- Unusual network behavior
- Unauthorized access attempts

The platforms also integrate monitoring with their broader security and compliance ecosystems.

#### Pricing Model

Azure Monitor and Log Analytics primarily use consumption-based pricing. Important cost factors include log ingestion, log retention, queries, alerts, and selected monitoring features. Microsoft offers different log plans and commitment options for larger ingestion volumes.

Amazon CloudWatch also uses consumption-based pricing. Costs can depend on the number of custom metrics, logs ingested, logs stored, dashboards, alarms, and API usage.

Google Cloud Monitoring and Logging similarly use usage-based pricing, with cost influenced by the amount and type of telemetry collected and retained.

A common cost-control strategy across all three platforms is to avoid collecting unnecessary logs indefinitely.

#### DevSecOps Integration

Monitoring is a critical part of a DevSecOps pipeline.

After an application is deployed, monitoring services can automatically detect failures, performance problems, and security-related events.

For example:

`Developer Commit → CI/CD Pipeline → Deployment → Monitoring → Alert → Investigation`

Azure Monitor integrates with Azure DevOps, GitHub, Logic Apps, Functions, and Sentinel.

CloudWatch integrates with AWS CodePipeline, Lambda, EventBridge, SNS, and other AWS services.

Google Cloud Monitoring and Logging integrate with Cloud Build, Cloud Functions, Pub/Sub, and Google Security Operations.

#### Analysis

The three monitoring platforms perform similar fundamental tasks.

Azure Monitor is especially convenient when an organization already uses Azure and Microsoft Sentinel because Log Analytics provides a common logging platform.

CloudWatch provides very strong native integration with AWS services.

Google Cloud separates monitoring and logging more visibly, but the services work closely together through Google's Cloud Operations environment.

---

#### 4. Azure Policy vs. AWS Config vs. Google Cloud Organization Policy

#### Overview

#### Microsoft Azure – Azure Policy

Azure Policy evaluates Azure resources against organizational rules.

Policies can require or prevent particular configurations. For example, an organization can create rules such as:

- Only deploy resources in approved regions
- Require specific resource tags
- Prevent creation of public IP addresses
- Require encryption
- Audit insecure configurations

Azure Policy supports effects such as **Audit**, **Deny**, and **Modify**.

This allows organizations to enforce governance before insecure or non-compliant resources are deployed.

#### AWS – AWS Config and Service Control Policies

There is no single AWS service that exactly duplicates Azure Policy.

**AWS Config** continuously records resource configurations and evaluates them using Config Rules.

**AWS Organizations Service Control Policies (SCPs)** establish permission guardrails across AWS accounts.

Together, these services provide functionality similar to Azure Policy.

AWS Config pricing is based primarily on configuration items recorded and rule or conformance-pack evaluations.

#### Google Cloud – Organization Policy Service

Google Cloud Organization Policy Service allows administrators to centrally define restrictions for resources within an organization.

Policies can be applied at different levels of Google's resource hierarchy:

`Organization → Folder → Project → Resource`

This is conceptually similar to the Azure hierarchy:

`Management Group → Subscription → Resource Group → Resource`

#### Core Features

| Feature | Azure Policy | AWS Config / SCP | Google Organization Policy |
|---|---|---|---|
| Resource governance | Yes | Yes | Yes |
| Compliance evaluation | Yes | AWS Config | Yes |
| Prevent deployments | Deny effect | SCP guardrails | Organization constraints |
| Audit mode | Yes | Config Rules | Policy/audit capabilities |
| Organizational hierarchy | Management Groups | AWS Organizations | Organization/Folders |
| Policy-as-code support | Yes | Yes | Yes |

##### Security and Compliance

Policy management helps organizations move security earlier in the development lifecycle.

Instead of detecting every insecure resource after deployment, governance controls can prevent insecure configurations from being created.

For example, a company could establish a policy:

> Production storage must not be publicly accessible.

A preventive policy can block the deployment instead of requiring the security team to discover it later.

This supports the DevSecOps idea of **shift-left security**.

#### Pricing Model

Azure Policy itself generally does not create a major direct policy-evaluation charge, although related services and remediation actions can create costs.

AWS Config uses consumption-based pricing based on configuration recording and compliance evaluations.

Google Organization Policy is part of Google Cloud resource governance, while other monitoring, logging, or security services used alongside the policies may generate charges.

#### DevSecOps Integration

Cloud policies are particularly useful in CI/CD environments.

For example:

`Terraform → CI/CD → Cloud Policy Evaluation → Deployment`

If the Terraform configuration violates organizational requirements, the platform can reject the deployment.

A practical strategy is to use less restrictive policies during development and stronger enforcement in production.

For example:

`Development: Audit`

`Production: Deny`

This gives developers visibility into policy violations without unnecessarily preventing experimentation, while production remains strongly protected.

#### Analysis

Azure Policy provides a very integrated policy-management experience inside Azure.

AWS generally requires multiple services to achieve the same result. AWS Config evaluates resource configurations, while SCPs provide organization-level permission boundaries.

Google Organization Policy provides a clean hierarchical model that resembles Azure Policy.

For organizations emphasizing policy-as-code and infrastructure-as-code, all three platforms can be incorporated into automated DevSecOps governance.

---

#### 5. Microsoft Defender for Cloud vs. AWS Security Hub vs. Google Security Command Center

#### Overview

#### Microsoft Azure – Defender for Cloud

Microsoft Defender for Cloud is a cloud-native security platform that helps organizations improve security posture and protect cloud workloads across Azure, hybrid, and multicloud environments.

It identifies security weaknesses, provides security recommendations, evaluates compliance, and detects threats.

One important concept is the **Secure Score**, which helps organizations identify security improvements.

#### AWS – AWS Security Hub

AWS Security Hub provides centralized visibility into cloud security findings and security posture.

It collects security findings from AWS services and supported third-party security products and helps organizations evaluate their AWS environment against security standards.

Security Hub therefore performs a role similar to Microsoft Defender for Cloud.

#### Google Cloud – Security Command Center

Google Cloud Security Command Center provides centralized security posture management and threat detection for Google Cloud environments.

It can identify vulnerabilities, misconfigurations, exposed resources, identity risks, and security threats.

Google describes Security Command Center as providing security capabilities for cloud and AI workloads, including cloud infrastructure entitlement management and security-posture capabilities.

#### Core Features

| Feature | Defender for Cloud | AWS Security Hub | Security Command Center |
|---|---|---|---|
| Security posture management | Yes | Yes | Yes |
| Misconfiguration detection | Yes | Yes | Yes |
| Security recommendations | Yes | Yes | Yes |
| Vulnerability information | Yes | Yes | Yes |
| Threat detection | Yes | Yes | Yes |
| Compliance dashboards | Yes | Yes | Yes |
| Multi-cloud capabilities | Yes | Increasing multi-cloud capabilities | Multi-cloud capabilities available |
| Central security score/posture | Secure Score | Security posture/findings | Security posture/findings |

#### Security and Compliance

These services help organizations continuously compare cloud environments against security standards and recommended configurations.

Defender for Cloud includes regulatory-compliance capabilities that allow organizations to monitor their compliance posture against assigned standards.

Typical checks can include:

- Publicly accessible resources
- Missing encryption
- Weak identity settings
- Vulnerable workloads
- Excessive permissions
- Missing security monitoring
- Unsafe network configurations

One important principle is that a high security score does **not** mean an environment is completely secure.

Security posture tools measure configured controls. They cannot guarantee that credentials will never be stolen, users will never make mistakes, or attackers will never find new vulnerabilities.

#### Pricing Model

Defender for Cloud provides some posture-management capabilities with Azure, while advanced workload protection uses paid Defender plans.

AWS Security Hub uses usage-based pricing. Depending on enabled functionality, charges can be based on security resources, findings, events, and security-data processing.

Google Security Command Center provides different service tiers. Premium capabilities can use subscription or pay-as-you-go pricing depending on the activation model.

#### DevSecOps Integration

Cloud security posture tools can continuously scan infrastructure created by deployment pipelines.

For example:

`GitHub → Terraform → Azure/AWS/GCP → Security Posture Scan → Finding → Automated Response`

Security findings can also trigger:

- Tickets
- Alerts
- Serverless functions
- Remediation workflows
- CI/CD actions
- SIEM investigations

This creates continuous security feedback instead of relying only on manual security reviews.

#### Analysis

Defender for Cloud is especially useful for organizations already using Azure because it integrates closely with Azure Policy, Azure Monitor, and Microsoft Sentinel.

AWS Security Hub is strongly integrated with the broader AWS security ecosystem.

Google Security Command Center offers similar security posture and threat-management capabilities for Google Cloud environments.

The three platforms follow the same general principle: continuously evaluate cloud resources and identify security weaknesses before they become serious incidents.

---

#### 6. Microsoft Sentinel vs. AWS Security Services vs. Google Security Operations

#### Overview

#### Microsoft Azure – Microsoft Sentinel

Microsoft Sentinel is Microsoft's cloud-native Security Information and Event Management (SIEM) platform.

It collects security information from many sources and allows security analysts to detect, investigate, hunt for, and respond to security threats.

Microsoft describes Sentinel as a cloud-native SIEM that combines threat detection, investigation, automation, threat intelligence, and proactive hunting.

It also provides Security Orchestration, Automation and Response (SOAR) capabilities.

#### AWS – Security Hub and Amazon Security Lake

AWS does not have one service that maps perfectly to Microsoft Sentinel.

The closest AWS architecture combines several services.

**AWS Security Hub** centralizes security findings and posture information.

**Amazon Security Lake** centralizes security logs and events from AWS, on-premises environments, SaaS platforms, and other cloud sources in a security-focused data lake.

Security Lake uses usage-based pricing for data ingestion and normalization.

Additional AWS services such as CloudWatch, EventBridge, Lambda, Detective, and partner SIEM solutions can be used for detection, investigation, and response.

Therefore, AWS provides the same general security architecture, but the functionality is distributed across multiple services.

#### Google Cloud – Google Security Operations

Google Security Operations is the closest direct GCP equivalent to Microsoft Sentinel.

It provides cloud-scale security analytics, SIEM capabilities, threat detection, investigation, and security response.

Google Security Operations can ingest Google Cloud security telemetry as well as information from many other environments and security products.

#### Core Features

| Feature | Microsoft Sentinel | AWS Security Services | Google Security Operations |
|---|---|---|---|
| SIEM | Yes | Distributed across services/partners | Yes |
| Central log ingestion | Yes | Security Lake/CloudWatch | Yes |
| Threat detection | Yes | Security Hub and related services | Yes |
| Threat hunting | Yes | Multiple AWS tools | Yes |
| Security automation | Logic Apps/playbooks | EventBridge/Lambda/automation | SOAR/playbooks |
| Incident investigation | Yes | Security Hub/Detective/etc. | Yes |
| Threat intelligence | Yes | AWS and partner integrations | Yes |
| Multi-cloud data | Yes | Security Lake/integrations | Yes |

#### Security and Compliance

A SIEM is valuable because individual security logs may not appear suspicious by themselves.

For example:

`10 failed logins → successful login → privileged operation → large data download`

Each event separately could be legitimate.

When the events are correlated, however, they could indicate that an attacker performed a brute-force or credential-compromise attack and then accessed sensitive data.

SIEM platforms allow security teams to correlate these events and investigate them as one security incident.

#### Pricing Model

Microsoft Sentinel is primarily usage based. Costs depend heavily on security-data ingestion and the underlying log analytics architecture, with commitment options available for organizations processing larger quantities of data.

AWS security analytics costs are distributed across the services used. Amazon Security Lake, for example, charges based on ingestion and normalization of supported AWS security data, with related storage and query services potentially generating additional charges.

Google Security Operations pricing depends on the selected security operations offering and enterprise agreement.

For SIEM systems, log volume is normally one of the most important cost considerations because security environments can generate very large amounts of telemetry.

#### DevSecOps Integration

SIEM and SOAR platforms provide the operational security layer of DevSecOps.

For example:

`Application → Security Logs → SIEM → Detection Rule → Incident → Automated Response`

A suspicious event could automatically trigger a response workflow such as:

1. Generate a security alert.
2. Open an incident.
3. Notify the security team.
4. Disable or restrict a compromised identity.
5. Block a malicious IP address.
6. Gather additional logs.
7. Create an investigation ticket.

This can significantly reduce response time compared with manual monitoring.

#### Analysis

Microsoft Sentinel offers one of the clearest integrated SIEM/SOAR experiences because detection, investigation, hunting, automation, and Microsoft security integrations are closely connected.

Google Security Operations is the closest direct Google equivalent because it is also designed as a large-scale security analytics and operations platform.

AWS takes a more modular approach. Security Hub, Security Lake, CloudWatch, EventBridge, Lambda, Detective, and other security services can be combined to create a similar architecture.

Therefore, describing **AWS Security Hub alone as a complete replacement for Microsoft Sentinel would not be completely accurate**.

---

#### 7. Overall DevSecOps Comparison

The services from all three providers can be placed into the same general DevSecOps security lifecycle.

```text
                 DEVSECOPS SECURITY LIFECYCLE

Developer
    |
    v
Source Code Repository
    |
    v
CI/CD Pipeline
    |
    +------ Identity and IAM
    |
    +------ Security / Policy Checks
    |
    v
Infrastructure Deployment
    |
    +------ Azure Policy
    +------ AWS Config / SCP
    +------ GCP Organization Policy
    |
    v
Running Cloud Environment
    |
    +------ Monitoring and Logs
    |
    +------ Security Posture Management
    |
    v
SIEM / Security Operations
    |
    v
Detection → Investigation → Response → Remediation
```

The major difference between the platforms is not whether they support DevSecOps, because all three do. The difference is how their individual services are organized and integrated.

---

#### 8. Overall Comparison

#### Microsoft Azure

#### Strengths

- Strong Microsoft ecosystem integration
- Entra ID provides powerful enterprise identity capabilities
- Azure Policy offers centralized governance
- Defender for Cloud integrates security posture and workload protection
- Microsoft Sentinel provides integrated SIEM and SOAR
- Strong integration between Monitor, Defender, Sentinel, Entra ID, Azure DevOps, and GitHub

#### Considerations

- Security licensing can become complex
- Large Log Analytics and Sentinel data volumes can create significant costs
- Organizations should carefully configure retention and ingestion policies

---

#### Amazon Web Services

#### Strengths

- Very granular IAM permission system
- Large security-service ecosystem
- Strong automation capabilities
- Strong integration with AWS Organizations
- CloudWatch provides extensive AWS monitoring
- Security Hub centralizes security findings

#### Considerations

- Security capabilities can be distributed across many services
- Some Azure services do not have a single direct AWS equivalent
- SIEM architectures may require Security Hub, Security Lake, CloudWatch, EventBridge, Lambda, and other services to work together

---

#### Google Cloud Platform

#### Strengths

- Strong identity and IAM model
- Simple hierarchical resource structure
- Integrated Cloud Logging and Monitoring
- Security Command Center provides centralized security posture management
- Google Security Operations provides enterprise SIEM and security analytics

#### Considerations

- Certain enterprise security capabilities require premium service tiers
- Organizations must understand the difference between Cloud Identity and Cloud IAM
- Some advanced security functionality is separated across several Google security products

---

#### 9. Final Comparison and Recommendation

Azure, AWS, and Google Cloud all provide mature security and compliance capabilities, but they organize those capabilities differently.

For **identity management**, Microsoft Entra ID offers a highly integrated enterprise identity platform, while AWS uses IAM Identity Center together with IAM and Google uses Cloud Identity together with Cloud IAM.

For **monitoring**, Azure Monitor, Amazon CloudWatch, and Google Cloud Monitoring and Logging offer similar capabilities for collecting telemetry, creating alerts, and troubleshooting systems.

For **cloud governance**, Azure Policy provides a very integrated policy engine. AWS achieves similar functionality using AWS Config and Service Control Policies, while Google Cloud uses Organization Policy.

For **security posture management**, Microsoft Defender for Cloud, AWS Security Hub, and Google Security Command Center all help organizations identify vulnerabilities, misconfigurations, and compliance problems.

For **SIEM and security operations**, Microsoft Sentinel and Google Security Operations provide relatively direct SIEM/SOAR platforms. AWS provides similar capabilities through a more modular combination of Security Hub, Security Lake, CloudWatch, EventBridge, Lambda, and other security services.

There is therefore no single cloud platform that is best in every situation. The appropriate platform depends on the organization's existing systems, technical expertise, compliance requirements, workload architecture, and budget.

An organization heavily invested in Microsoft technologies may benefit from Azure because of the integration among Entra ID, Azure Policy, Defender for Cloud, Monitor, and Sentinel. An organization operating primarily AWS workloads may benefit from AWS's highly granular IAM system and modular security architecture. Organizations using Google's cloud ecosystem may prefer Google Cloud because of its IAM model, Security Command Center, and Google Security Operations.

Most importantly, security should not depend on one product. Effective cloud security requires multiple layers including identity management, least privilege, governance policies, monitoring, vulnerability management, SIEM, automation, and continuous improvement.

---

#### 10. Conclusion

From my learning in the couse, the comparison among kinds of cloud service, demonstrates that the major cloud providers address the same fundamental security problems but use different service architectures.

Microsoft Azure tends to provide tightly integrated security services within the Microsoft ecosystem. AWS provides highly granular and modular services that can be combined to build customized security architectures. Google Cloud provides strong centralized security and data analytics capabilities through Cloud IAM, Security Command Center, and Google Security Operations.

From a DevSecOps perspective, all three platforms support automation, policy-as-code, continuous monitoring, identity-based access control, security assessment, and automated incident response.

The most important lesson is, therefore not simply memorizing equivalent product names. Cloud security professionals need to understand the **security capability** that each service provides. Once the underlying security requirement is understood, equivalent services can be identified and implemented across different cloud platforms.