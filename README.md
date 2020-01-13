## **LP Threat Modeling Outline**

#### Use the [LP Threat Modeling Template](./Templates/Threat_Model_Template.md) to fill out the following information

1. __Define the Scope and Application Objectives__
	* Define the Scope
	    - To what extent the threat model will cover
	    - A threat model scope defines what is relevant, within a particular view
	        * There can be multiple scopes, or views, that pertain to a single application
	        * Typically there should be two scopes: Application and Infrastructure
	            - The application scope is the use case / application's functionality
	            - The infrastructure scope consists of how the application is compiled, tested, and stood up
	* Define the Purpose of the Application
	    - What functions the application provides
	* Define Business Objectives of the Application
	    - How this application benefits the business
	* Define the Application's Security Tier
	    - Tiers range from 1 to 3, with Tier 1 being the minimum that all software must adhere to
	    - This tiering system is derrived from [OWASP's Application Security Verification Standard v3.0.1](https://www.owasp.org/images/3/33/OWASP_Application_Security_Verification_Standard_3.0.1.pdf), pages 8-12
	        * Reference the ASVS for more detail on the following tiers and a checklist of requirements for each level
	    - Tier 1 applies to general software
	        * Coincides with ASVS Level 1
	        * The software must adequately defend against application security vulnerabilities which are easy to discover
	            - Refer to OWASP Top 10 and other similar checklists
        - Tier 2 applies to applications that contain sensitive data or controls
	        * Coincides with ASVS Level 2
            * The software must have effective security and monitoring controls in place, which are used within the application
            * The software must adequately defend against most risks associated with software to date
        - Tier 3 applies to applications that perform critical functions, where failure could significantly impact the organization's operations and/or survivability
	        * Coincides with ASVS Level 3
            * The software must adequately defend against advanced application security vulnerabilities
            * The software must demonstrate principles of good security design
	* Define Compliance Requirements
2. __Decompose the Application__
	* Draw/Update Control Flow Diagrams using the [Diagram Syntax](./Templates/Threat_Modeling_Syntax.md)
		- Application Threat Model Diagram ([Example ATMD 1](https://raw.githubusercontent.com/executionByFork/LP_ThreatModeling/master/Templates/Example_Application_Diagram.jpg)) ([Example ATMD 2](https://raw.githubusercontent.com/executionByFork/LP_ThreatModeling/master/Templates/Example_Application_Diagram2.png))
		    * Diagram of how the app works in production
		    * Use case diagram / data flow diagram
		- Infrastructure Threat Model Diagram ([Example ITMD 1](https://raw.githubusercontent.com/executionByFork/LP_ThreatModeling/master/Templates/Example_Infrastructure_Diagram.jpg)) ([Example ITMD 2](https://raw.githubusercontent.com/executionByFork/LP_ThreatModeling/master/Templates/Example_Infrastructure_Diagram2.png))
		    * Diagram of the system infrastructure and how the app is deployed
	* List user roles and their permissions
	    - This is a list of what actions each role *should* be able to do
3. __Identify Assets__
	* Identify Assets
	    - Items/areas of interest to an attacker
	    - The things that this application needs to secure
	* Identify External Dependencies
	    - external entities that would keep the application from functioning properly if removed
4. __Identify Threats and Analyize Risk__ 
	1. Create a Threat Traceability Matrix ([Example TTM](./Templates/Threat_Traceability_Matrix.csv))
	    - The simplest way to create this is to use Excel and save the matrix as a CSV file, then throw the CSV into a [markdown table generator](https://donatstudios.com/CsvToMarkdownTable)
	    - Look at each asset individually while considering which categories of [STRIDE](https://en.wikipedia.org/wiki/STRIDE_(security)) **may** apply. Remember, this is a list of *potential* threats to the application, and not neccesarily a list of things the app is currently vulnerable to. 
    		* __S__poofing
    		* __T__ampering
    		* __R__epudiation
    		* __I__nformation Disclosure
    		* __D__enial of Service
    		* __E__levation of Privilege
		- Play the [Elevation of Privilege card game](Templates/EoP_Card_Game.pdf)
		- Each threat should be listed as a new row in the Threat Matrix, which has the following columns
    	    - STRIDE Category
    	    - Interaction (Connection details between the user and the application using the [Interaction Syntax](./Templates/Threat_Modeling_Syntax.md))
    	    - Exploit Description (The type of attack performed by the malicious user)
    	    - Attack Surface (All of the different points where an attacker could get in and get data out)
    	    - Impact (What is the impact if this is exploited)
    	    - Mitigation (How can we stop or prevent this threat)
	2. Reorder the threat traceability matrix from highest to lowest risk
	   - Security Tier 1 applications
	        - Rank threats relative to each other to get a comparative list
	   - Security Tier 2 applications
	        - Rank threats numerically with the [5x5 Risk Matrix](./Templates/5x5_Risk_Matrix.png)
	        - Likelihood Ranking Definitions
                * __Rare__: it may not happen in a lifetime
                * __Unlikely__: this will occur every so often
                * __Moderate__: it will happen regularly
                * __Likely__: this will be a frequent problem
                * __Almost Certain__: it will happen constantly
            - Consequence Ranking Definitions
                * __Insignificant__: slight, possibly unnoticeable impact. Business unaffected, maybe a phone call is needed
                * __Minor__: temporary loss of service that does not affect the customer. Business experiences a hiccup in operations
                * __Significant__: loss of sensitive data or service for an extended amount of time, possible financial loss
                * __Major__: major loss of sensitive data or an interuption of critical services, business will experience financial loss
                * __Severe__: complete destruction or theft of data and rendering a service unrecoverable. Extreme impact to the business and it's survivability
	   - Security Tier 3 applications
	        - Rank threats using the [CVSS](https://www.first.org/cvss/)
	        - [Online CVSS Calculator](https://nvd.nist.gov/vuln-metrics/cvss/v3-calculator)

## **Assessing the Threat Model**
#### How good is the threat model?

How to assess the threat model's effectiveness based on the Application's Security Tier:
* Tier 1 Application
    - General reflection on the artifacts generated
* Tier 2 Application
    - General reflection like in Tier 1 with additional self-performed penetration tests
* Tier 3 Application
    - Professional penetration test

