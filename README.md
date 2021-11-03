# Kenna - SecureX Incident Enrichment

IT operations are still very manual today. Customers are always challenged to maintain system health and improve online security. This workflow demonstrates how Cisco SecureX orchestration can be leveraged to automate vulnerability management.

This workflow periodically checks SecureX incidents for Threat Detected Events from Cisco Secure Endpoint. When an incident is returned, the workflow collects all observations from it and reaches to Kenna Security for vulnerabilities information related to executed malware. If information is returned, the workflow updates the incident in SecureX to document the findings. This workflow is designed to run every 5 minutes on a schedule.

**Target Group:** Default TargetGroup

**Targets:** CTR_For_Access_Token, Private_CTIA_Target, Kenna_Target

**Steps:**
[] Fetch incidents from SecureX

[] For each incident:

[]> Extract the observations and target

[]> Search for the asset in Kenna by IP and fetch its asset ID

[]> Fetch asset risk score, priority and vulnerabilities by asset ID

[]> Find all malware associated with open vulnerabilities matching criteria: malware exploitable, has active new breaches and popular targets.

[]> Compare with malware in the SecureX incident. If match found, update the incident with Kenna information. Add tags and notes to Kenna asset to link with the incident.
