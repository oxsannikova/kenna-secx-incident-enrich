![License: CISCO](https://img.shields.io/badge/License-CISCO-blue.svg)
[![published](https://static.production.devnetcloud.com/codeexchange/assets/images/devnet-published.svg)](https://developer.cisco.com/codeexchange/github/repo/<REPO-HERE>)

# Kenna - SecureX Incident Enrichment Automation

IT operations are still very manual today. Customers are always challenged to maintain system health and improve online security. This workflow demonstrates how Cisco SecureX orchestration can be leveraged to automate vulnerability management.

## Features

This workflow periodically checks SecureX incidents for Threat Detected Events from Cisco Secure Endpoint. When an incident is returned, the workflow collects all observations from it and reaches to Kenna Security for vulnerabilities information related to executed malware. If information is returned, the workflow updates the incident in SecureX to document the findings. This workflow is designed to run every 5 minutes on a schedule.

> **Note:** Please test this properly before implementing in a production environment. This is a sample workflow!

## Preprequisites

In order to leverage Kenna Security malware intelligence for detected vulnerabilities, Kenna Security VI+ License is required.

## Steps

[] Fetch incidents from SecureX

[] For each incident:

[]> Extract the observations and target

[]> Search for the asset in Kenna by IP and fetch its asset ID

[]> Fetch asset risk score, priority and vulnerabilities by asset ID

[]> Find all malware associated with open vulnerabilities matching criteria: malware exploitable, has active new breaches and popular targets. (Kenna Security VI+ License required)

[]> Compare with malware in the SecureX incident. If match found, update the incident with Kenna information. Add tags and notes to Kenna asset to link with the incident.

## Required Targets and Target Groups

* Target Group: Default TargetGroup

* Targets: CTR_For_Access_Token, Private_CTIA_Target, Kenna_Target

## Required Account Keys

* Account Keys: CTR_Credentials

## Required Global Variables

* Secure String: Kenna - Token

## Required Local Variables
* Update Kenna URL local varilable with your Kenna Security instance domain name (e.g. <customername>.<region>.kennasecurity.com) in order to properly construct pivot links for Kenna pages.

## Required Atomic Workflows

* Kenna-GetAssetID
* Kenna-GetAssetVulnerabilities
* Kenna-ShowMalwareHashes
* Kenna-ShowVulnerabilityDefinition
* Kenna-TagAnAsset
* Kenna-UpdateAssetNotes

## Setup instructions

### Configure Global Variables

1. Browse to your SecureX orchestration instance. This will be a different URL depending on the region your account is in: 

* US: https://securex-ao.us.security.cisco.com/orch-ui/workflows/
* EU: https://securex-ao.eu.security.cisco.com/orch-ui/workflows/
* APJC: https://securex-ao.apjc.security.cisco.com/orch-ui/workflows/

2. In the left hand menu, select **Variables**.

3. Click **New Variable**. Data Type - **Secure String**. Name **Kenna - Token**.

4. Provide your Kenna API token.

>**Note:** For more information on Kenna Security APIs, check out [API Reference](https://apidocs.kennasecurity.com/reference).


### Import atomic actions

1. In the left pane menu, select **Workflows**. Click on **IMPORT** to import the workflow:

![](assets/import-workflow.png)

2. Click on **Browse** and copy paste the content of the [Kenna-GetAssetID json file](https://raw.githubusercontent.com/oxsannikova/kenna-secx-incident-enrich/main/Kenna-GetAssetID__definition_workflow_01PS8IPKGRMLM4SBCSvH0gnwesjU3qZn8tK/definition_workflow_01PS8IPKGRMLM4SBCSvH0gnwesjU3qZn8tK.json) file inside of the text window. Select **IMPORT AS A NEW WORKFLOW (CLONE)** and click on **IMPORT**.

![](assets/copy-paste.png)

3. Repeat step 2 for the rest of Atomic actions: [Kenna-GetAssetVulnerabilities](https://raw.githubusercontent.com/oxsannikova/kenna-secx-incident-enrich/main/Kenna-GetAssetVulnerabilities__definition_workflow_01PS92J4863DX7ifHF01heFerwmqnoTJ2YI/definition_workflow_01PS92J4863DX7ifHF01heFerwmqnoTJ2YI.json), [Kenna-ShowMalwareHashes](https://raw.githubusercontent.com/oxsannikova/kenna-secx-incident-enrich/main/Kenna-ShowMalwareHashes__definition_workflow_01PSAG3UACQ1N38Q4Bns45cYWo4hpBsqNGv/definition_workflow_01PSAG3UACQ1N38Q4Bns45cYWo4hpBsqNGv.json), [Kenna-ShowVulnerabilityDefinition](https://raw.githubusercontent.com/oxsannikova/kenna-secx-incident-enrich/main/Kenna-ShowVilnerabilityDefinition__definition_workflow_01PT1JRLJ5QHH3Fb3lctaK2Uqk40TuL4ldW/definition_workflow_01PT1JRLJ5QHH3Fb3lctaK2Uqk40TuL4ldW.json), [Kenna-TagAnAsset](https://raw.githubusercontent.com/oxsannikova/kenna-secx-incident-enrich/main/Kenna-TagAnAsset__definition_workflow_01PT35JR1M1EX3nOhjfiu2AXQ7u1scMmHmf/definition_workflow_01PT35JR1M1EX3nOhjfiu2AXQ7u1scMmHmf.json), [Kenna-UpdateAssetNotes](https://raw.githubusercontent.com/oxsannikova/kenna-secx-incident-enrich/main/Kenna-UpdateAssetNotes__definition_workflow_01PT3O5HVQHTM4rskgSAYVYEl6EZbT7vZit/definition_workflow_01PT3O5HVQHTM4rskgSAYVYEl6EZbT7vZit.json).

### Import main workflow

1. In the left pane menu, select **Workflows**. Click on **IMPORT** to import the workflow.

2. Click on **Browse** and copy paste the content of the [Kenna-SecureXIncidentsEnrichmentWF](https://raw.githubusercontent.com/oxsannikova/kenna-secx-incident-enrich/main/Kenna-SecureXIncidentsEnrichmentWF__definition_workflow_01PS6ZOQJ757L4tTyTL407ymLunCPJgdOLW/definition_workflow_01PS6ZOQJ757L4tTyTL407ymLunCPJgdOLW.json) file inside of the text window.  Select **IMPORT AS A NEW WORKFLOW (CLONE)** and click on **IMPORT**.

3. Go to **My Workflows** and open the main workflow **Kenna - SecureX Incidents Enrichment**. In the properties on the right hand-side, find section **Triggers**. You will see that the status is - **Disabled**. Click on the name of the Trigger and change the status to **Enabled**.

## Notes

* Please test this properly before implementing in a production environment. This is a sample workflow!
* In order to leverage Kenna Security malware intelligence for detected vulnerabilities, Kenna Security VI+ License is required.

## Author(s)

* Oxana Sannikova, Security Technical Solutions Architect (Cisco)
