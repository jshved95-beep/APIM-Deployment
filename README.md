# Production APIM Infrastructure

## Architecture
<svg viewBox="0 0 1400 900" xmlns="http://www.w3.org/2000/svg">
  <!-- Define styles -->
  <defs>
    <style>
      .azure-box { fill: #0078D4; stroke: #004578; stroke-width: 2; }
      .service-box { fill: #E8F4FD; stroke: #0078D4; stroke-width: 2; }
      .keyvault-box { fill: #FFE8CC; stroke: #FF8C00; stroke-width: 2; }
      .monitoring-box { fill: #E6F3E6; stroke: #107C10; stroke-width: 2; }
      .network-box { fill: #F0E6FF; stroke: #5C2D91; stroke-width: 2; }
      .text-title { font-family: Arial, sans-serif; font-size: 16px; font-weight: bold; fill: #000; }
      .text-label { font-family: Arial, sans-serif; font-size: 13px; fill: #333; }
      .text-small { font-family: Arial, sans-serif; font-size: 11px; fill: #666; }
      .arrow { stroke: #666; stroke-width: 2; fill: none; marker-end: url(#arrowhead); }
      .arrow-data { stroke: #0078D4; stroke-width: 2; fill: none; marker-end: url(#arrowhead-blue); stroke-dasharray: 5,5; }
    </style>
    <marker id="arrowhead" markerWidth="10" markerHeight="10" refX="9" refY="3" orient="auto">
      <polygon points="0 0, 10 3, 0 6" fill="#666" />
    </marker>
    <marker id="arrowhead-blue" markerWidth="10" markerHeight="10" refX="9" refY="3" orient="auto">
      <polygon points="0 0, 10 3, 0 6" fill="#0078D4" />
    </marker>
  </defs>

  <!-- Title -->
  <text x="700" y="30" text-anchor="middle" class="text-title" style="font-size: 20px;">Production-Ready APIM Infrastructure</text>
  
  <!-- Environment Labels -->
  <text x="100" y="80" class="text-label" style="font-weight: bold;">Multi-Environment:</text>
  <rect x="250" y="65" width="60" height="25" rx="3" fill="#E8F4FD" stroke="#0078D4"/>
  <text x="280" y="82" text-anchor="middle" class="text-small">Dev</text>
  <rect x="320" y="65" width="60" height="25" rx="3" fill="#FFE8CC" stroke="#FF8C00"/>
  <text x="350" y="82" text-anchor="middle" class="text-small">Staging</text>
  <rect x="390" y="65" width="60" height="25" rx="3" fill="#E6F3E6" stroke="#107C10"/>
  <text x="420" y="82" text-anchor="middle" class="text-small">Prod</text>

  <!-- Resource Groups Container -->
  <rect x="50" y="110" width="1300" height="750" rx="5" fill="#F5F5F5" stroke="#999" stroke-width="2" stroke-dasharray="5,5"/>
  <text x="70" y="135" class="text-label" style="font-weight: bold;">Azure Resource Group (per environment)</text>

  <!-- VNET Container -->
  <rect x="80" y="160" width="1240" height="300" rx="5" class="network-box"/>
  <text x="100" y="185" class="text-label" style="font-weight: bold;">Virtual Network (Optional)</text>

  <!-- API Management -->
  <rect x="120" y="210" width="280" height="220" rx="5" class="service-box"/>
  <text x="260" y="235" text-anchor="middle" class="text-title">API Management</text>
  
  <!-- APIM components -->
  <rect x="140" y="250" width="240" height="40" rx="3" fill="white" stroke="#0078D4"/>
  <text x="260" y="273" text-anchor="middle" class="text-label">Gateway</text>
  
  <rect x="140" y="300" width="110" height="35" rx="3" fill="white" stroke="#0078D4"/>
  <text x="195" y="320" text-anchor="middle" class="text-small">Products</text>
  
  <rect x="260" y="300" width="120" height="35" rx="3" fill="white" stroke="#0078D4"/>
  <text x="320" y="320" text-anchor="middle" class="text-small">APIs & Policies</text>
  
  <rect x="140" y="345" width="240" height="35" rx="3" fill="white" stroke="#0078D4"/>
  <text x="260" y="365" text-anchor="middle" class="text-small">Managed Identity</text>
  
  <text x="260" y="405" text-anchor="middle" class="text-small" style="font-style: italic;">Rate limiting, JWT validation</text>
  <text x="260" y="420" text-anchor="middle" class="text-small" style="font-style: italic;">CORS, IP restrictions</text>

  <!-- Backend Services -->
  <rect x="480" y="210" width="200" height="220" rx="5" class="service-box"/>
  <text x="580" y="235" text-anchor="middle" class="text-title">Backend APIs</text>
  
  <rect x="500" y="260" width="160" height="40" rx="3" fill="white" stroke="#0078D4"/>
  <text x="580" y="283" text-anchor="middle" class="text-small">Internal Services</text>
  
  <rect x="500" y="310" width="160" height="40" rx="3" fill="white" stroke="#0078D4"/>
  <text x="580" y="333" text-anchor="middle" class="text-small">External APIs</text>
  
  <rect x="500" y="360" width="160" height="40" rx="3" fill="white" stroke="#0078D4"/>
  <text x="580" y="383" text-anchor="middle" class="text-small">Microservices</text>

  <!-- NSG -->
  <rect x="750" y="210" width="180" height="100" rx="5" fill="#F0E6FF" stroke="#5C2D91" stroke-width="2"/>
  <text x="840" y="235" text-anchor="middle" class="text-title">Network Security</text>
  <text x="840" y="260" text-anchor="middle" class="text-small">NSG Rules</text>
  <text x="840" y="280" text-anchor="middle" class="text-small">IP Whitelisting</text>
  <text x="840" y="300" text-anchor="middle" class="text-small">Private Endpoints</text>

  <!-- Private DNS -->
  <rect x="750" y="330" width="180" height="100" rx="5" fill="#F0E6FF" stroke="#5C2D91" stroke-width="2"/>
  <text x="840" y="355" text-anchor="middle" class="text-title">Private DNS Zone</text>
  <text x="840" y="380" text-anchor="middle" class="text-small">azure-api.net</text>
  <text x="840" y="400" text-anchor="middle" class="text-small">Name Resolution</text>

  <!-- Key Vault -->
  <rect x="1000" y="210" width="280" height="220" rx="5" class="keyvault-box"/>
  <text x="1140" y="235" text-anchor="middle" class="text-title">Azure Key Vault</text>
  
  <rect x="1020" y="260" width="240" height="40" rx="3" fill="white" stroke="#FF8C00"/>
  <text x="1140" y="283" text-anchor="middle" class="text-small">Secrets</text>
  
  <rect x="1020" y="310" width="115" height="35" rx="3" fill="white" stroke="#FF8C00"/>
  <text x="1077" y="330" text-anchor="middle" class="text-small">API Keys</text>
  
  <rect x="1145" y="310" width="115" height="35" rx="3" fill="white" stroke="#FF8C00"/>
  <text x="1202" y="330" text-anchor="middle" class="text-small">Certificates</text>
  
  <rect x="1020" y="355" width="240" height="35" rx="3" fill="white" stroke="#FF8C00"/>
  <text x="1140" y="375" text-anchor="middle" class="text-small">Connection Strings</text>
  
  <text x="1140" y="410" text-anchor="middle" class="text-small" style="font-style: italic;">RBAC: Managed Identity access</text>

  <!-- Monitoring Stack -->
  <rect x="120" y="490" width="560" height="340" rx="5" class="monitoring-box"/>
  <text x="400" y="520" text-anchor="middle" class="text-title">Observability & Monitoring Stack</text>

  <!-- Log Analytics -->
  <rect x="150" y="540" width="240" height="120" rx="5" fill="white" stroke="#107C10" stroke-width="2"/>
  <text x="270" y="565" text-anchor="middle" class="text-label" style="font-weight: bold;">Log Analytics</text>
  <text x="270" y="590" text-anchor="middle" class="text-small">APIM Diagnostic Logs</text>
  <text x="270" y="610" text-anchor="middle" class="text-small">Request/Response Logs</text>
  <text x="270" y="630" text-anchor="middle" class="text-small">KQL Queries</text>
  <text x="270" y="650" text-anchor="middle" class="text-small">Custom Dashboards</text>

  <!-- Application Insights -->
  <rect x="420" y="540" width="240" height="120" rx="5" fill="white" stroke="#107C10" stroke-width="2"/>
  <text x="540" y="565" text-anchor="middle" class="text-label" style="font-weight: bold;">Application Insights</text>
  <text x="540" y="590" text-anchor="middle" class="text-small">Performance Metrics</text>
  <text x="540" y="610" text-anchor="middle" class="text-small">Dependency Tracking</text>
  <text x="540" y="630" text-anchor="middle" class="text-small">Failure Analysis</text>
  <text x="540" y="650" text-anchor="middle" class="text-small">Distributed Tracing</text>

  <!-- Alerts and Cost -->
  <rect x="150" y="680" width="240" height="120" rx="5" fill="white" stroke="#107C10" stroke-width="2"/>
  <text x="270" y="705" text-anchor="middle" class="text-label" style="font-weight: bold;">Azure Monitor Alerts</text>
  <text x="270" y="730" text-anchor="middle" class="text-small">Availability Alerts</text>
  <text x="270" y="750" text-anchor="middle" class="text-small">Performance Thresholds</text>
  <text x="270" y="770" text-anchor="middle" class="text-small">Error Rate Monitoring</text>
  <text x="270" y="790" text-anchor="middle" class="text-small">Action Groups</text>

  <rect x="420" y="680" width="240" height="120" rx="5" fill="white" stroke="#107C10" stroke-width="2"/>
  <text x="540" y="705" text-anchor="middle" class="text-label" style="font-weight: bold;">Cost Management</text>
  <text x="540" y="730" text-anchor="middle" class="text-small">Resource Tags</text>
  <text x="540" y="750" text-anchor="middle" class="text-small">Cost Allocation</text>
  <text x="540" y="770" text-anchor="middle" class="text-small">Budget Alerts</text>
  <text x="540" y="790" text-anchor="middle" class="text-small">Optimization Reports</text>

  <!-- IaC and CI/CD -->
  <rect x="750" y="490" width="570" height="340" rx="5" fill="#FFF4E6" stroke="#D83B01" stroke-width="2"/>
  <text x="1035" y="520" text-anchor="middle" class="text-title">Infrastructure as Code & CI/CD</text>

  <!-- Terraform -->
  <rect x="780" y="550" width="250" height="260" rx="5" fill="white" stroke="#D83B01" stroke-width="2"/>
  <text x="905" y="575" text-anchor="middle" class="text-label" style="font-weight: bold;">Terraform</text>
  
  <rect x="800" y="595" width="210" height="35" rx="3" fill="#E8F4FD" stroke="#0078D4"/>
  <text x="905" y="615" text-anchor="middle" class="text-small">Modules (reusable)</text>
  
  <rect x="800" y="640" width="210" height="35" rx="3" fill="#E8F4FD" stroke="#0078D4"/>
  <text x="905" y="660" text-anchor="middle" class="text-small">Remote State (Azure Storage)</text>
  
  <rect x="800" y="685" width="210" height="35" rx="3" fill="#E8F4FD" stroke="#0078D4"/>
  <text x="905" y="705" text-anchor="middle" class="text-small">Workspaces (dev/stg/prod)</text>
  
  <rect x="800" y="730" width="100" height="30" rx="3" fill="#FFE8CC" stroke="#FF8C00"/>
  <text x="850" y="748" text-anchor="middle" class="text-small">variables.tf</text>
  
  <rect x="910" y="730" width="100" height="30" rx="3" fill="#FFE8CC" stroke="#FF8C00"/>
  <text x="960" y="748" text-anchor="middle" class="text-small">*.tfvars</text>
  
  <rect x="800" y="770" width="210" height="30" rx="3" fill="#E6F3E6" stroke="#107C10"/>
  <text x="905" y="788" text-anchor="middle" class="text-small">terraform.tfstate (remote)</text>

  <!-- GitHub Actions / Azure DevOps -->
  <rect x="1060" y="550" width="240" height="260" rx="5" fill="white" stroke="#D83B01" stroke-width="2"/>
  <text x="1180" y="575" text-anchor="middle" class="text-label" style="font-weight: bold;">CI/CD Pipeline</text>
  
  <rect x="1080" y="595" width="200" height="30" rx="3" fill="#E8F4FD" stroke="#0078D4"/>
  <text x="1180" y="613" text-anchor="middle" class="text-small">GitHub Actions / ADO</text>
  
  <text x="1180" y="645" text-anchor="middle" class="text-small" style="font-weight: bold;">On Pull Request:</text>
  <text x="1180" y="665" text-anchor="middle" class="text-small">• terraform fmt</text>
  <text x="1180" y="682" text-anchor="middle" class="text-small">• terraform validate</text>
  <text x="1180" y="699" text-anchor="middle" class="text-small">• terraform plan</text>
  
  <text x="1180" y="725" text-anchor="middle" class="text-small" style="font-weight: bold;">On Merge:</text>
  <text x="1180" y="745" text-anchor="middle" class="text-small">• terraform apply (dev auto)</text>
  <text x="1180" y="762" text-anchor="middle" class="text-small">• Manual approval (stg/prod)</text>
  <text x="1180" y="779" text-anchor="middle" class="text-small">• Drift detection</text>
  <text x="1180" y="796" text-anchor="middle" class="text-small">• State locking</text>

  <!-- Arrows showing data flow -->
  <!-- APIM to Backend -->
  <path d="M 400 320 L 480 320" class="arrow"/>
  
  <!-- APIM to Key Vault -->
  <path d="M 400 350 Q 700 350 1000 350" class="arrow-data"/>
  <text x="700" y="340" text-anchor="middle" class="text-small" fill="#0078D4">Managed Identity</text>
  
  <!-- APIM to Monitoring -->
  <path d="M 260 430 L 260 540" class="arrow-data"/>
  <text x="220" y="480" text-anchor="end" class="text-small" fill="#0078D4">Diagnostic Logs</text>
  
  <!-- Backend to App Insights -->
  <path d="M 580 430 L 540 540" class="arrow-data"/>
  
  <!-- Terraform manages everything -->
  <path d="M 905 550 L 260 430" class="arrow" stroke-dasharray="3,3"/>
  <path d="M 905 550 L 1140 430" class="arrow" stroke-dasharray="3,3"/>
  <path d="M 905 550 L 270 490" class="arrow" stroke-dasharray="3,3"/>

  <!-- Legend -->
  <rect x="50" y="870" width="600" height="20" fill="none"/>
  <text x="60" y="885" class="text-small" style="font-weight: bold;">Key Features:</text>
  <text x="150" y="885" class="text-small">• Multi-environment isolation • Secure secrets management • Full observability • IaC with GitOps • Cost optimization tags</text>

</svg>
## Features
- Multi-environment deployment (dev/staging/prod)
- Secrets management via Key Vault
- Full observability stack
- Security hardening (managed identity, RBAC, policies)
- Cost optimization (tags, appropriate SKUs)

## Prerequisites
- Azure subscription
- Terraform >= 1.5
- Azure CLI

## Deployment


## Cost Estimate


## Design Decisions


## Future Enhancements
