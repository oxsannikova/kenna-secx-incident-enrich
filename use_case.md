# Kenna - SecureX Incident Enrichment Automation

IT operations are still very manual today. Customers are always challenged to maintain system health and improve online security. This workflow demonstrates how Cisco SecureX orchestration can be leveraged to automate vulnerability management. 

### Watch a demo of this use case [here](https://youtu.be/01iojxIb-_g)!

## Features

This workflow periodically checks SecureX incidents for Threat Detected Events from Cisco Secure Endpoint. When an incident is returned, the workflow collects all observations from it and reaches to Kenna Security for vulnerabilities information related to executed malware. If information is returned, the workflow updates the incident in SecureX to document the findings. This workflow is designed to run every 5 minutes on a schedule.

## SecureX orchestration workflow repository

* SecureX orchestration provides a no-to-low code approach for building automated workflows. 
* These workflows can interact with various types of resources and systems, whether they’re from Cisco or a third-party. 
* This repository contains atomic actions and workflows that can be imported into SecureX orchestration as well as a variety of documentation.

### Atomic Actions
* Atomic actions are self-contained workflows that are similar to a function in traditional programming. 
* They can consume input, perform various actions, and then return output. 
* They’re designed to be portable, re-usable, and make building workflows more efficient.

## Workflows
* Workflows are the larger component of orchestration and are similar to a script in traditional programming. 
* A workflow can be simple and only have a few actions or be complex and string together many different actions for different products.

### Business Case

Service-oriented orchestration provides the agility to model and act on IT services. These features make creating orchestration active and dynamic, and allow for:

* Defining new, higher-level services in the system, and deploy new services quickly.
* In real-time, after these new types of services have been defined, creating real-time instances of those new services.
* Using events to watch for patterns in these services, enabling policy-driven automation.
* Service-oriented Orchestration combines several industry trends to synthesize a fresh approach to orchestration:

Please continue your reading in this [SecureX white paper](https://www.cisco.com/c/en/us/products/collateral/security/white-paper-c11-744498.html).

### Related Sandbox
Currently there is no DevNet sandbox yet, however you can find all options to try out [SecureX orchestration](https://developer.cisco.com/learning/lab/Cisco-SecureX-101-lab/step/1) here!

### List of SecureX Learning Labs
* Please try out this [SecureX DevNet learning lab](https://developer.cisco.com/learning/modules/SecureX-orchestration) to try this yourself. 
* Please also check out the [SecureX microsite](https://developer.cisco.com/securex/) on DevNet!

### Solutions on Ecosystem Exchange
Please check out related solutions on [DevNet Ecosystem Exchange](https://developer.cisco.com/ecosystem/solutions/#key=securex).
