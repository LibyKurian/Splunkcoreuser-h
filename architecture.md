flowchart TD

  %% Sources
  A1[Endpoints<br/>(Laptops, Desktops)]
  A2[Servers<br/>(Web, App, DB)]
  A3[Network Devices<br/>(Firewall, Router)]
  A4[Cloud Services<br/>(AWS, Azure)]
  A5[Applications<br/>(ERP, CRM)]
  
  %% Collection
  B1[Syslog, WEF, API Collection]
  
  %% Aggregation & Enrichment
  C1[Log Aggregation<br/>(Logstash / Fluentd)]
  C2[Parsing & Enrichment<br/>(GeoIP, Threat Intel)]
  
  %% Storage
  D1[Distributed Log Storage<br/>(ElasticSearch, S3)]
  
  %% Threat Intel
  D2[Threat Intelligence<br/>(Feeds, IOC)]
  
  %% SIEM
  E1[SIEM Platform]
  
  %% Outputs from SIEM
  F1[SOAR Platforms<br/>(Cortex XSOAR, Splunk Phantom)]
  F2[Dashboards & Reporting]
  F3[Team Workstations<br/>(L1 - L3 Analysts)]
  
  %% Automation & Logic
  G1[Playbook Automation]
  G2[Automated Ticket Creation]
  G3[Conditional Logic]
  G4[Analyst Reviews & Escalation]
  
  %% Actions if met
  H1[Block IP]
  H2[Isolate Endpoint]
  H3[Delete Phishing Email]
  H4[Enrich with Threat Intel]
  
  %% Feedback and resolution
  I1[Feedback & Logging]
  I2[Incident Resolution]
  
  %% Connections from sources to collection
  A1 --> B1
  A2 --> B1
  A3 --> B1
  A4 --> B1
  A5 --> B1
  
  %% Collection to Aggregation
  B1 --> C1
  C1 --> D1
  C1 --> C2
  
  %% Enrichment to storage and threat intel
  C2 --> D1
  C2 --> D2
  
  %% To SIEM
  D1 --> E1
  D2 --> E1
  
  %% SIEM outputs
  E1 --> F1
  E1 --> F2
  E1 --> F3
  
  %% SOAR to Playbook
  F1 --> G1
  G1 --> G2
  
  %% Automation logic
  G2 --> G3
  G3 --|condition met| H1
  G3 --|condition met| H2
  G3 --|condition met| H3
  G3 --|condition met| H4
  G3 --|condition not met| G4
  
  %% Both flows lead to feedback and resolution
  H1 --> I1
  H2 --> I1
  H3 --> I1
  H4 --> I1
  G4 --> I1
  I1 --> I2
