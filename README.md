# CLoud-2

#LOT	#	Label	Requirements	Scope	SOFASEC	Security requirement	implementation of control in run phase	Activities	Activities preparation	DoD	Associated Tools	Proofs	Frequency of the run check	"Communication with CSRO
At the begining of the RUN phase, the first POC for the RUN team will be the CSRO for each FT"	Automated workflow / tools	Workflow steps	Relevant outputs	How to improve the control (Global governance to unify the control methodology)	further information on the control of CSRO	Scorecard KPI	Recheck (Y/N)
1	1	X0	Code security review	"Control plane
Ressource plane
Run a code security review for both"	8. code review	Automated code security review must be implemented in the CI/CD pipeline (done for vulnerabilities within Python, dependancies, and secret mgmt)	"Modification or not of the source code : For each repository, run SoFaSec 

Use SoFaSec on each repository tagued by the CSRO as critical, even if the source code has not been modified (appearance of a new vulnerability)
Feature Team Endpoint API code must be stored in a dedicated sGithub repository, to be scanned

Use Bandit within the CI/CD pipeline in blocking mode 

There is a daily automated SoFaSec scan on every reporsitories, for every XaaS. 
A manual assessment of falses-positives is realized, and reporting to Analyics"	"SG Bandit : What is the Bandit version, how is called Bandit, are there nosec or Skip (control bypass), is report sent to sonarqube
https://sgithub.fr.world.socgen/sec-cls/repos_analysis

1. Validate the weekly scan results and mitigation plan
2. Mitigation plan follow-up with FT
3. Update the date of the control"	"Ensure that the CI/CD chain is functional
Specify the dedicated sGithub to identify all the involved repositories
Inform the CSRO of the tests to be carried out
Access to Github to scan repositories (local copy within the test VM)
Access to evidence already deposited on the labeling board (JIRA). Jira is the only tool requiring an access account.
Use of the tool developed in this way (repository analysis) -> Centralization of results and export to the security dashboard (analytics security)"	"A SAST has been realized (with false-positive managed)
Check if the json report has been generated and exported, same thing about export to Sonarqube. The audit results must be exported to Analytics platform for each CSRO and FT
For a major new release, the same audit activities than RUN control phase will be realized, but within a new labelization process "	"SG Bandit
Sonarqube
Jenkins"	"1. For the first iteration of the run phase, it is nevertheless proposed to realize this control in order to validate those realized during the labeling process (keep in mind that SOFASEC is run every day, but without manual check of results)
2. Thanks to the dedicated tool, the script returns the version of SG bandit deployed on repository (in order to get a screen shot)
3. Sccreen shot of the export to Sonarqube
4. Audit report  :
 - specify the name of the repository (endpoint API)
 - Screen shot of call to Bandit
 - Pipfile (package dependency management), so imports requirements.txt type files into Pipfile
5. In presence of vulnerabilities, provide an action plan (from FT) -> Curently, generic mitigations are provided by auditor. Then, same results will be provided directly by the Sofasec scripts (work in progress)"	Daily, with an automated process based on Sofasec and associated scripts, to run scan and export results to Analytics	"Weekly security committee with CSRO, FT, G3C : 
1. Is there any issue about the implementation of SG Bandit or the CI/CD pipeline ?
2. Is the coverage rate 100% compared to SGithub's repositories ?
3. Explainations of G3C for the vulnerabilities and scan results 
4. Are there untreated vulnerabilities ?
5. Status of the previous mitigation plan

The results of SOFASEC scans will be exported to Analytics. These results must be checked weeckly by the CSRO, the PO and the SM , especialy regarding the high and very high vulnerabilities levels.this implies an acknowledgement by the feature team

In the same way, the daily scan results will be assessed by G3C. A phase of false-positive will be realized, and the restitution will be made for each CSRO-FT weekly"	"Dedicated tool (realization), for Bandit -> SoFaSec
Eagle eye (Mgmt of the risks and vulnerabilities)
Analytics security (for a global overview of the security KPI)"	"Instal environment (Python, Bandit, …)
Audit realization
Report and sharing contents
Mgmt of the false-positives in the results (G3C) 
Mitigation plan defined by the automation of the result writting and shared with G3C + CSRO + FT
Application of the mitigation plan (FT)
Monitoring of the mitigation plan (CSRO)
Recheck"	"•	Weekly Report on SG_Bandit usage to FT/CSRO: %Repositories scanned per FT (report available)
•	Improve SG_Bandit usage rate : 100% FT have to use SG_Bandit on all repositories using python (create and track JIRA request to FT)
•	Improve SG_Bandit SonarQube integration rate : 100% FT with SG_Bandit integrated to SonarQube (create and track JIRA request to FT)
• Number of vulnerabilities founded for each repo (and total)
• Assess there is no skip or Nosec in the scan results
• Verify that vulnerabilities have been addressed 
•	Daily report to FT/CSRO on bandit findings per FT : # findings per repo and FT 
•	Qualify and communicate to CSRO bandit findings details : 100% findings analyzed and corrected"	"Curently, Sofasec is ran every day, and produce raw results, shared within Analytics
Today and tomorrow, the Sofasec scripts will be improved (refine commands for a coverage and relevance increased, filter certain results, …), same things for a proposal of mitigation plan for each kind of vulnerability identified. Results will be shared with analytics, with a view for vulnerabilities (and other Sofasec KPI) and another one for the mitigation plan. The SG_Bandit scoring is already used understand the results, and to help the FT to prioritise the mitigation plan

A generic mitigation for each vulnerability is already defined in SG_Bandit. It will easier to understand and define the dedicated mitigation plan
Sofasec scan will still be ran every day."	" - Feature Team Endpoint API code is stored is this sGithub repository
Point the main repository. Don't forget to include all repositories, even those considered secondary
 - Repository code is Python, see the curent version 
Check the version of Python
 - Static Application Security Testing (SAST) is performed by Bandit on the CI/CD chain.
Check the SG Bandit version
 - SAST is systematically performed in blocking mode during deployment, and there are no skips and the 7 #nosec tags are validated by the CSRO.
Ensure that the SoFaSec Framework is implemented (8. Code security check : Latest version of Sg_bandit is implemented on all python repositories in blocking mode. Keep in mind to identify (and justify) each Skip or #Nosec
 - SAST reports are sent to SonarQube for reporting and alerting when vulnerabilities are detected.
Ensure that every reports are sent to Sonarqube
 - No vulnerabilities have been identified at date (CSRO validation) / or / X vulnearbilities have been identified : See the dedicated action plan 
Ensure that a false-positive results have been assessed by a dedicated process (to send to the CSRO and the FT only the relevant results)"	" - 1st level : % of conformity
 - 2nd level : 
 > % of repositories on wich SG Bandit is installed
 > % of repositories on wich the latest version of SG Bandit is installed
 > Number of vulnerabilities for each repository 
 > Number of vulnerabilities for repositories that impacted by several vulnerabilities (especialy high and very high levels)"	Recheck to be done to validate the vulnerabilities fixing. It is automaticaly realized through the dailly scans
2	2	X0	Internal security audit	"Control plane
Ressource plane
The risk analysis must cover both environments"		"Ensure that the risk analysis is up2date for both environments
For a new technology/component used within the XaaS, a new labelization will be realized regarding an update of the  risk analysis, and a dedicated pentest "	"Risk analysis (ARA) must be realized as soon as a modification is made for the XaaS context, and at least annually if it is not, and validation realized by a CSRO.
Only few modifications can be treated within the RUN phase, and if there is no modification made during the year, a quick check will be realized once a year (introduce the types of changes that are subject to revision in the RUN) :
A change in the ARA could be treated within the RUN phase if :
The change concerns a component, configuration, dependency, type of data or access (...) that leads to change the gravity impact or probability of a threat scenario, and therefore a (downward) risk. If the risk is increased, a new labellization must be realized
Please note: If a significant modification of the ARA is made, a new labelization must be realized."	"ARA: Check if the ARA is updated
RAF: Only for the high and very high risks. Check if this sheet is updated
Monthly report of the status of mitigation plan in EE

1. Check for significant/minor modification in ARA
2. If YES, initiate a new labelization
3. If NO, validate and update ARA & FSR
4. Collect the proofs, update the date of control and the results in Eagle Eye"	"ARA modified : 
 - Significant modification -> New labelization managed by CSRO (Risk increased after the change)
 - Simple modifications -> Modification documented by FT, validated by owner of the RUN control
ARA not modified:
Owner of the RUN control realize a quick check once a year, to ensure that the details of the previous ARA are still relevants

Access to evidence already deposited on the dedicated team mind (ARA, RAF)
The global risk dashboard is available through Eagle Eye"	"If the ARA isn't changed, at least annually, collect the associated proof (RAF, ARA, …) and update the control

For each minor change, collect the associated proof (RAF, ARA, …), valid them within the ARA updated by FT"	"Mind
Eagle Eye"	"ARA, RAF updated by FT, and validated by the CSRO

The formalism of these documents is the same as that usually defined by SG during the labelling phases"	"If there is no modification of the XaaS environment, at least once a year (to update the validation of the ARA in the same context of use) 
In accordance with each feature team (and CSRO), as soon as a new version is developed, or if a new vulnerability is identified, or in occurence of a security incident, the ARA revision will be realized in a labelization context (irelevant for RUN activities)
-> Weekly for the follow-up of the mitigation plan but already covered by the control#28
-> Once a year for the ARA"	"Annual security committee with each stakeholders : 
1. Any update on the XaaS (Infrastructure, …) ?
2. Risk analysis updated ?
3. Appearance of new risks (risks increased) ?

Each PI :
3. Mitigation plan status"	Eagle eye (Mgmt of the risks)	"The CSRO knows and follows the mitigation plan
All the CSRO can feed EE with the details of a labellization phase. Then the owner of the RUN control could consolidate the results :
 - Follow if all the actions are closed during the dedicated PI, and if they're still opened, check the reason and the date of completion)
 - Realize the actions defined to check if the ARA is updated (with and without changes during the year)"	"Monthly report of the status of mitigation plan

ARA and EE contents uptated when a change is made for the XaaS context
Dates of annual control updated in ARA and EE"	"Curently the results of ARA are followed into EE, with several usefull information regarding the mitigation plan.
The owner of the action is at entity level (FT and PO), and the planning of action is at PI level

If necessary, specific information could be more detailed for a finer follow-up of the actions (in EE for example)"	"A Risk analysis has been done by the CSRO during the labellization phase
Check with the FT if there is some modification of the ARA.
If there is, check the ARA and enssure that is not significant changes (do not show an increased risk). Then, verify the absence of high or very high risks, verify if a defined mitigation plan has been defined (all actions must be closed), update the date of the control

If  not, check the ARA, verify the absence of high or very high risks, verify if a defined mitigation plan has been defined (all actions must be closed), update the date of the control
The Feature Team has completed the FSR
Check the FSR, and validate it
If a residual riskat high or very high level is still identified, a derogation or a justification must be detailled within the RAF, and must be validated by the security team

All these item must be reachables from the dedicated Mind. The Follow up of the mitiation must be relized with EE"	" - 1st level : % of actions closed
 - Number of new actions

 - 2nd level : 
 - Number of High risks
 - Number of medium risks
 - Number of low risks "	Monthly recheck must be done to validate the action closed  (follow up of the mitigation plan), and update of the details in Eagle Eye
2	3	X0	Peer Code Review	"Control plane
Ressource plane
Ensure that a peer code review is realized for both "	4. Peer review	Peer code review is enforced (through pull requests and reviewers)	"Development activities are realized by the development teams
Check if the peer code review is implemented within the CI/CD pipeline for each repository, in blocking mode to validate the commit of code source.
Then, check if for each release the peer code review has been correctly used with the dedicated process, previously checked by the CSRO."	"Check within the repositories if the peer review is still enforced for all sensitive operations and if the peer review is realized for each modification of code or minor release
Check if the dedicated process is still used within the FT, and if he's documented (still the same that used for the initial labelization)

1. Check if the dedicated process is still used within the FT for peer review
2. If NO, work with FT to create/Impement/update the dedicated workflow and processheck if some peer reviews were realized on new releases
3. If YES, check if some peer reviews were realized on new releases
4. Check if a peer code review is done
4.1. If YES, validate the peer reviews, collect all the proofs and outputs, update the control date
4.2. update the date of the control
5. If NO, update the date of the control"	"Access to the source code 
Access to the Github configuration
Documented process
Ensure that the associated activities are documented and shared on sgithub for all branches"	"For each major release, collect the associated proof (Check within each repositories if the peer review has been realized, in compliance with the dedicated process established for the initial labellization).
To merge commit, the code cannot be integrated to main branches unless peer review has been realized and approved."	"Sgithub
JIRA"	" - Screenshot of repo setting enforcing peer review (or of the main folder to have only one screen shot, especialy if there is several repositories within it)
 - Git flow documentation mentioning review process
 - Detail about the 4 eyes review (names of reviewers, details of the passed check status, dates)"	At least once a year, to ensure that the dedicated process is still used within the CI/CD chain	"Annual security committee with each CSRO : 
1. Is  the dedicated process still used within the FT for peer review
2. Are some peer revies realized on new releases ?
3. % of repositories for which a peer review has been realized during last year, in compliance with the dedicated process"	Github	At the and of a dev iterration, before each triying of merge a commit, a second dev must validate the code to be allowed to be integrated to main branches (Automatic workflow that could create a ticket asking a peer revew, one of the dev team member shall take the ticket and realize the peer review during the timeslot defined)	Report of the mitigation plan updated (if needed)	The traceability of the name of the two developpers that realized the peer code review 	"Peer code review is systematically performed by a member of the FT and is mandatory for merging pull requests
Check if a dedicated process is defined within the FT (If existing, put the link within the Jira card and the report)
Check if the peer review is enforced for all sensitive operations and if the peer review is realized (The SS must be added to the report), same thing for the pull requests"	" - Peer code review enforced on repositories (Y/N)
 - Peer code review realized"	No
2	4	X0	Data classification	"Control plane
Ressource plane
Ensure that the sensitive data handled are classified "		Confidentiality classification of data handled by the XaaS	"Ensure that the data classification has not changed, at least once a year. If any change is realized for this item, a new labelization must be realized
"	"Check the FSR and the public documentation (RTD) 
Check if these documents have been edited and reviewed (if there is no evolution, the check shall be realized once a year)

1. Check if there is any change in Data Classification
2. If YES, validate the FSR and RTD
3. If NO, update the date of control"	"Be acquainted with the SG data classification standard.
Compare with the previous version of the labelization/control"	"The initial documentation must be formalized and detail the kind and the level of datas handled.
An annual review must be realized, to validate that these level are still the same. Then make the consolidation and the reporting "	FSR 	The date of the FSR and XaaS documentation are reviewed	"In accordance with each feature team (and CSRO), as soon as a component is modified/added, wich could have an impact on the data classification (or with new data or new data  classification level, handled by the XaaS). 
And if there no change, at least once a year"	"Annual security committee with each stakeholders : 
1. Any update on the XaaS wich could have an impact on the data classification ?
2. RAF and documentation updated ?"	RAF	If there is no change about the data classification, just check if the documentation and RAF dates have been updated (check to be realized once a year if during the months no change have been identified)	Monthly report of the RAF updated (and XaaS documentation if relevant)		"FSR have been established by FT (available on Mind)
Check the FSR and the details about the data classification
Data classification has been used to establish the risk analysis
Check if the data classification is a data considered to realize the risk assessment (Confidentiality and integrity) 
The DICP is XXXX (available on Platform documentation)
Check if the DICP level is compliant with the data classification defiened
If C2 or C3 data level are handled by the XaaS, justify it (controle plane, ressource plane, type, ...) "	" - Level of datas handled
 - % of data identified, classified, and up2date"	"No
Based on the documents completed by the FT initialy, and checked by G3C team"
1	5	X0	FT secret management	"Control plane
Ressource plane
Identify the tool used to store the secrets, and verify the absence of credentials in the source code"	3. Secret mgmt (see the control #1)	"Assess the adequacy of the solution used to manage the secrets, ensure that no credentials apears within the source code (use Trufflehog)
Ensure that the FT defined a password lifecycle process (for each turn over, the password must be changed)"	"The secret storage solution is defiened  during the labellization phase.
For each turnover within the FT, a check will be realized to assess that the new member use the defiened tools.

For each code modification, check if secret or credentials doesn't apears within the source code

Use secret scan tools on CI/CD in order identify non-compliant commits (about secrets)"	"Identify the maner to store FT secrets (Vault or keepass) -> How to use them? Personal credentials, not shared, stored within a personal vault or keepass, with a dedicated access. Avoid the team keepass to store the secrets used to access to the FT platform/tools, ...

For any turnover in the team, change the shared passwords

Assess if theses activities are realized on the basis of the dedicated process (defined during the initial labelization phase)

Trufflehog : Scan repositories recursively and files (history and branches) for secrets . Set the max commit depth to go back to search secrets (1000)
https://github.com/dxa4481/truffleHog/blob/dev/README.md

Trufflehog :
1. Validate the weekly scan results and mitigation plan
2. Folow-up of the mitigation plan
3. Update the date of control

Secret storage solution :
1. Check if Secrets / Credentials are still stored in dedicated solution
2. If YES, update the date of the control
3. If No, check if the FT applied the dedicated process for the storage of the FT secrets
4. update the date of the control"	Check the initial labelization report (what is the storage tool used by the FT / each member - What is the dedicated process for the mgmt of the FT credentials)	SOFASEC (Secret mgmt.): Identify the solution (Vault or other) and scan involved repositories with dedicated tools (Trufflehog)	"Vault/secret
Keepass
Trufflehog"	"1. Secret storage solution (Keepass or Vault) despcription
2. Associated IAM matrix
3. Audit report
4. Backup solution description"	"For the feature team, as soon as there is a turnover in the team

At least once a year, the good application of the dedicated process for the secret mgmt will be realized by the CSRO

Weekly for the exploitation of the Trufflehog scans results"	"Annual security committee with each CSRO : 
1. Is a new member of the team arrived?
2. Are its secrets stored with the dedicated tool ?

Weekly :
3. Scan the repositories, and follow-up the results / mitigation plan 
"	"Dedicated tool (realization), for Trufflehog
Eagle eye (Mgmt of the risks and vulnerabilities)
Analytics security (for a global overview of the security KPI)"	"Instal environment (Trufflehog, …)
Audit realization
Report and sharing contents
Mgmt of the false-positives in the results (G3C) 
Mitigation plan defined by the automation of the result writting and shared with G3C + CSRO + FT
Application of the mitigation plan (FT)
Monitoring of the mitigation plan (CSRO)
Recheck

Assess if the secret storage tool is still the same than for the initial labelization, same thing about the dedicated process
Assess if the turno over in the FT is realized on the basis of the process, and use the dedicated tool"	"•	Monthly report on Secret findings to FT/CSRO : #findings per repo per FT (report available)
•	Daily report on new finding to CSRO : findings per repo per FT 
•	Qualify and communicate to CSRO secret findings : 100% findings analyzed and corrected
•	Create security incident when relevant (specify involved criteras)"	"Define a lifecycle for the pwd (policy)
Identify the way to access to all psw (local, shared, …)
Check the modification in case of turn over for ex"	" - FT members secret are stored on a SG validated solution, localy or remotly  (Local Keepass, CyberArk secret mgmt tool, ...), and backed-up by the corporate desktop backup solution)
Check if the used solution is validated by the group (CyberArk, Keepass), and if the backup solution is relevant in the context
 - Each member has his own keepass, with his own master key. There is no sharing of Keepass
Check if each FT members use their own Keepass (no shared Keepass must be used)  
If service accounts are used, they could be stocked within a team Keepass. The master Pwd of this one must be defined and stocked
 - The Keepass contains secrets used to manage the XaaS components
Check the kind of secrets stored within keepass"	" - 1st level : % of conformity
 - 2nd level : 
 > % of repositories impacted with secrets founded within repositories
 > % of accounts using a valid tool to store secrets
 > % of accounts using a valid backup solution "	Recheck to be done to validate the vulnerabilities fixing 
1	6	X0	XaaS secret management	"Control plane
Ressource plane
Identify the tool used to store the customers secrets, and verify the absence of credentials in the source code"	Secret mgmt (see the control #1)	Identify the tool used to store the customers secrets, ensure that no credentials apears within the source code (use Trufflehog)	"Use the dedicated tools to assess for each repository if any customers secrets are still available within the code

Use secret scan tools on CI/CD in order identify non-compliant commits (about secrets)"	"Identify the maner to store customer secrets. Give some details about it (wo can access it, how, …)
Ensure that the secrets/credz are not stored in the source code, not accessible by unauthorized person, not appears in clear on filesystem or backups

Trufflehog : Scan repositories recursively and files (history and branches) for secrets . Set the max commit depth to go back to search secrets (1000 by default)
https://github.com/dxa4481/truffleHog/blob/dev/README.md

Trufflehog :
1. Validate the weekly scan results and mitigation plan
2. Folow-up of the mitigation plan
3. Update the date of control

Secret storage solution :
1. Check if customer secrets are still stored in dedicated solution
2. If YES, update the date of the control
3. If No, check if the FT applied the solution for the storage of the customer secrets
4. update the date of the control"	Check the initial labelization report (what is the storage tool used for the customers  - What is the dedicated process for the mgmt of the customers credentials)	SOFASEC (Secret mgmt.): Identify the solution and scan involved repositories with dedicated tools (Trufflehog)	Trufflehog	"1. Secret storage solution despcription
2. Store details about the master key, the associated ACL, the key mgmt details, backup details
3. Audit report
4. Backup solution description"	"At least once a year, the good application of the dedicated process for the secret mgmt will be realized by the CSRO

Weekly for the exploitation of the Trufflehog scans results"	"Annual security committee with each CSRO : 
1.  Are its secrets stored with the dedicated tool ?
2. Is a new realease planned ?
3. Scan the new realease repositories 
4. Store details about the master key, the associated ACL, the key mgmt details, backup details

Weekly checks with SOFASEC"	"Dedicated tool (realization), for Trufflehog
Eagle eye (Mgmt of the risks and vulnerabilities)
Analytics security (for a global overview of the security KPI)"	"Instal environment (Trufflehog, …)
Audit realization
Report and sharing contents
Mgmt of the false-positives in the results (G3C) 
Mitigation plan defined by the automation of the result writting and shared with G3C + CSRO + FT
Application of the mitigation plan (FT)
Monitoring of the mitigation plan (CSRO)
Recheck"	"•	Monthly report on Secret findings to FT/CSRO : #findings per repo per FT (report available)
•	Daily report on new finding to CSRO : findings per repo per FT 
•	Qualify and communicate to CSRO secret findings : 100% findings analyzed and corrected
•	Create security incident when relevant (specify involved criteras)"		"All secrets are managed in Societe Generale's XaaS Vault or Secret platform 
Check if a SG solution is used
Passwords/secrets are pushed as environment variables at each deploy (for example by ansible playbook)
Check how the pwd pushing is enforced 
The FT declares no secrets exposed/used in the source code
Check the report writted by the FT to assess if no secrets are founded within the code source"	" - 1st level : % of conformity
 - 2nd level : 
 > % of repositories impacted with secrets founded within repositories
 > Using a valid tool to store secrets (Y/N)
 > Using a valid backup solution (Y/N) "	Recheck to be done to validate the vulnerabilities fixing 
2	7	X0	Architecture documentation	"Control plane
Ressource plane
Define the architecture for both and give some security details"		Architecture documentation must be definied by the FT, validated by CSRO, and must include security baseline	"Describe the XaaS architecture in the Platform RTD
Check if the architecture documentation is formalized, available and up2date"	"Check if the architecture documentation has changed during the year

Check if all IP@ and FQDN (fully qualified domain name), aministrator and data interfaces are correctly completed within the architecture document, and are all up2date

1. Check if there is any change in Architecture Documentation
2. If YES, validate the Architecture Document and RTD
3. If NO, update the date of the control"	"Minimal information to obtain for the architecture documents validation :

 - XaaS description in the context of Cloud Plateform
 - The control plane structure (including architecture and functional diagrams)
 - The resource plane structure (including architecture and functional diagrams)
 - The links and flows between control and resource plane
 - The links and flows between control and resource plane and others XaaS
 - OSI level 2 and 3 architecture diagrams - flow matrices  
 - filtering rules  
 - The security data classification and data model
 - Control Plane API components
 - Network flow table
 - Environments segregation (network, access control)
"	Check if the architecture documentation is formalized, with the needed details, if they are validated by the CSRO and up2date		Architecture documentation	"As soon the architecture is changed

Once a year if no change is identified"	"Annual security committee with each CSRO : 
1.  Is the architecture document formalized ? Validated by the CSRO ? Updated ?
2. Is an architecture change planned?"	Check the documents within the dedicated Git - JIRA that contain proofs	If there is no change about the architecture, just check if the documentation have been updated (check to be realized once a year if during the months no change have been identified)	Architecture documentation updated, reviewed by the CSRO at least once a year, at the anniversary date of labellization	"Platform architecture standard : What are the requirements of this standard ?
 - Architecture and functional diagrams and description (data flow matrix, zones, hosts, IP@, ...)
 - A description of each components and their role
 - The security data classification
 - The Conceptual Data model (if relevant)
 - Some use cases
 - Resiliency details of the solution (BCP + DRP)
 - SLA
The architecture documentation must be controled and validated by the CSRO for the initial labelization, and then, for each major evolution (...of the architecture, so of the associated documentation)."	" - The architecture documentation is available in the platform documentation
 - The defined elements are described within the architecture documentation
 - The documentation is up to date 
 - The relevant items have been tested and validated (FT and CSRO), like the resiliency mechanisms, ..."	 - Achitecture documentation updated : Y/N	"No
Based on the documents completed by the CSRO"
2	8	X0	Product documentation	"Control plane
Ressource plane
Ensure that the documentation is available  "		Product documentation must be formalized by the FT and validated by CSRO	Check if the product documentation is formalized, available and up2date	"Check if for the ressource plane and control plane a user guide is formalized. This guide must describe the IAM roles (IAM Matrix role vs privileges), the swagger with API interface description (standard specification : Design, build, test, standardize)

1. Check if there is any change in Product Documentation
2. If YES, validate the Product document and RTD
3. If NO, update the date of the control"	"Minimal information to obtain for the product documents validation :

 - User guide
 - Swagger (with the details of each API calls)
 - Description of the roles/scopes in Swagger page"	Check if the product documentation is formalized, with the needed details, if they are validated by the CSRO and upd2date		Product documentation	"As soon the product is changed (enough to justify a documentation modification)

Once a year if no change is identified"	"Annual security committee with each CSRO : 
1.  Is the product document formalized ? Validated by the CSRO ? Updated ?
2. Is a product change planned?"	Check the documents within the dedicated Git - JIRA that contain proofs	If there is no change about the product, just check if the documentation have been updated (check to be realized once a year if during the months no change have been identified)	Product documentation updated, reviewed by the CSRO at least once a year, at the anniversary date of labellization	"Product documentation standard : Must contain :
 - User guide and swagger detailled
 - Roles/Scopes appears in the swagger page (or getting started to ease the onboarding of users)"	" - The produt documentation is available (RTD)
 - The defined elements are described within the product documentation
 - The documentation is up to date 
 - The relevant items have been tested and validated (FT and CSRO), like swagger and user guide "	 - Product documentation updated : Y/N	"No
Based on the documents completed by the CSRO"
2	9	X0	Bastion	"Control plane
Ressource plane
Ensure that the FT access to any backend component (for both) through a bastion"		For control plane and resource plane, mandatory bastion usage for XaaS administration activities	"Identify all the administration tools available and used for all XaaS (Checklist)
Identify the bastion used by the FT members
Ensure that the SOC cover the XaaS perimeter for any access to an asset through a bypass of bastion
Check the cuttoff for the administrator accounts (CyberArk)"	"Check if all administrator interfaces are only reachables through a bastion (no direct access must be realized)
Check the cutt off status for the accounts

1. Once a year, check if there is any change in the Bastion and the associated use
2. If YES, validate the usage of Bastion and the relevant documents
3. Update the date of control
4. If NO, just update the date of control
5. Twice a year, check if the cut-off of privileged accounts (CyberArk) is finished
6. If YES, update the date of control
7. If NO, follow-up with the FT of the finalization of accounts cutt-off"	Ensure with the FT that the cut-off for the priviliged accounts is finished / in way to be be finished soon	Check if the Bastion documentation is formalized, with the needed details, if they are validated by the CSRO and upd2date. They must include the details about the administration interfaces, the selected Bastion, the onboarded profiles, the network filtering rules applied...		"1. XaaS documentation about the bastion use
2. Any details about the use of the bastion (Screen shot of administration interfaces for example)
3. Reports about the bybass of the bastion send by SOC (direct accesses realized by the FT) validated by the CSRO"	In accordance with each feature team (and CSRO), as soon as a modification is realized about the Bastion used, or the administration interfaces	"Annual security committee with each CSRO : 
1. Any modification for the Bastion?
2. Any possible bypass of the bastion ?"	Check the documents within the dedicated Git - JIRA that contain proofs	If there is no change about the Bastion and the associated use, just check if the documentation have been updated (check to be realized once a year if during the months no change have been identified)	XaaS documentation about the bastion use updated, reviewed by the CSRO at least once a year, at the anniversary date of labellization		" - Specify what is the bastion used by the XaaS/FT, for priviliged accounts and the associated ACL
 - Specify any exception/derogation
 - Validate that is not possible to reach the hosts in avoiding the bastion (directly from a developer or administrator workstation through a SSH connexion) 
 - The CyberArk cut-off (if CA is used) must be defined, detailling the accounts for the XaaS"	" - First view : Use of a bastion to access to assets
 -Second vew : XaaS (Bastion use) documentation updated : Y/N"	"No
Based on the documents completed by the CSRO"
2	10	X0	Using PKI	"Control plane
Ressource plane
Ensure for both that is used TLS based communications rely on an approved PKI certificate"		All XaaS components using TLS certificates must use GTS validated solution for TLS certificates management.	"Check if the XaaS use the PKIaaS for certificates mgmt
Same thing about virtual appliances

FT must use a Golden source (Marley) type reference system in order to identify all the assets deployed on the XaaS perimeter, and to provide an export of the certificates (on DIN) used to make a differential between the 2 sources. CSRO must check these items"	"A particular attention is paid to SAN (subject alternative name) and CN (common name) certificates

1. Check if there is any change about the PKI/certificates & the associated use
2. If YES, check if Certificates used by the platform are provided by authorized service
3. Update the date of control
4. If NO, directly update the date of control"	Retrieve the list of official SG certificate authorities	"Check if the XaaS components use PKIaaS
check if all certificates are issued by an official SG CA (Self signed certificates are forbiden on production environments)
Check the validity of each certificates, regarding the SG standards"		"1. List of certificates used on the XaaS (type, reference, period of validity, …)
2. Report containing the CSRO review about the validity of the used certificates"	"In accordance with each feature team (and CSRO), as soon as a modification is realized about the PKI/certificates used
If there is no modification, at least once a year"	"Annual security committee with each CSRO : 
1. Any update on the XaaS wich could have an impact on the certificates used ?
2. Dedicated documentation updated (list of certificates and CSRO report) ?"		If there is no change about the KPI/certificates and the associated use, just check if the documentation have been updated (check to be realized once a year if during the months no change have been identified)	XaaS documentation about the PKI/certificate use updated, reviewed by the CSRO at least once a year, at the anniversary date of labellization. The certificates, based on the SG standards, are valid during a certain period of time		" - Certificates used by the platform are provided by the Certificate Cloud Pltaform Service
 - Certificates could be also provided by the PKIaaS platform
 - The certificates could be sent through Ansible (dedicated service) 
 - The certificates must be checked with the dedicated tool (Qualys SSL Labs ?) to assess their compliance with SG standard (what are they?) and good practices. 
 - The details of the certificates could be checked (by sampling) with the following items :
1. Period of validity
2. Issuing Certification authority 
3. Object (field for wich the certificate is issued)
4. Use of the key
5. Information on the certification revocation list
6. Signature and hash algorithms about encryption"	 - % of conformity about the certificates used	"Yes
If non-compliance is identified, a recheck is needed to ensure that the apropriates certificates are used"
2	11	X0	Traceability of production accesses through API	"Control plane
Ensure for control plane the user interactions with the API are logged"		Have traceability of all actions concerning the XaaS API	"Check if the identified activities are logued within metrology (customers interractions with the API)
The details of actions and API accesses logued must be provided by the FT, and validated by the CSRO"	"Check the matrix (activities, events, errors, accesses and system logs vs logs sent) formalized by the FT, validated by CSRO. 
Ensure that all technical logs at API level are generated and sent to Metrology (Check Ansible or other dedicated tool)

-> These checks must be realized as soon as a change is realized for the API calls (new logs). If there is no change, check once a year

1. Check if there is any change in matrix and logging mechanism
2. If YES, check and validate the matrix and the API traceability to MaaS
3. Collect all the Proofs and update the date of control
4. If NO, directly collect all the Proofs and update the date of control"	"Retrieve the list of all actions for wich it is relevant to get logs  (Customer interractions with the API only)
Retrieve the list of API calls for each XaaS (for a customer use), and API requests for a specific action on the backend using a service account
These lists are formalized for the initial labelization. The RUN control is just a check for any update"	"Check if the solution used to log API interactions is still the same
Check if the list within metrology of all the interactions realized by customers on the API service are listed and the associated logs are produced
"	"Kibana
Ansible
Metrology"	"1. Automated report (script, for example with blackbox) containing the details about the log strategy for the XaaS (up2date, if no change, validate it once a year)
2. Screenshot of log configuration sent to metrology (Only if there is changes, otherwise validate it once a year) 
3. check the new call API, at the swagger level, to record new logs (see the blackbox platform to view the logs)"	"In accordance with each feature team (and CSRO), as soon as a modification is realized about the actions/perimeter whose it is relevant to log activities.
If no modification, a recheck must be performed once a year"	"Annual security committee with each CSRO : 
1. Any update on the XaaS wich could have an impact on the actions logged ?
2. If yes the dedicated documentation must be updated (list of actions logged) "	Log strategy could be accessed and ditributed through Ansible and Kibana	If there is no change about the way to log interactions and their associated use, just check if the documentation (list of API logs) have been updated (check to be realized once a year if during the months no change have been identified)	XaaS documentation about the logs updated, reviewed by the CSRO at least once a year, at the anniversary date of labellization	"This control can be carried out by the Feature Team independently. 
If changes are made to the API (added or deleted logs) an update must be performed and validated by the CSRO. If no changes are made during the year, a simple check of the previous status will be carried out by the CSRO on the basis of the elements provided by the FT"	"If there is no change during the year, make a quick check of the elements shared by the FT for the initial labelization :

 - Check the Log strategy for the XaaS (up2date, if no change, validate it once a year)
 - Check the list/matrix of all actions/event that produce a log (API calls, ...) 
 - Check if these elements are mentioned within the screenshot of log configuration sent to metrology (up2date, if no change, validate it once a year)
 - Check through Kibana the XaaS log strategy pushed (directly if an access is provided, or through a screen shot)
"	 - % of interactions identified logged	"Yes
If non-compliance is identified, a recheck is needed to ensure that all the relevant actions are logged"
2	12	X0	Using platform IAM for access control	"Control plane
Ressource plane
Ensure that the actions go through the IAM platform"	2. Access Control on CI/CD and environments	Use GTS IAM to control the operations on the XaaS (Whats, Access Control)	Check if IAMaaS is used for each access/scope of the XaaS	"Check that there is a script to make calls to the IAM.
Check the scopes used (in relation to what is defined in the swagger => Check if for the ressource plane and control plane a documentation describe the IAM roles and privileges)

-> These checks must be realized as soon as a change is realized for the IAM accesses. If there is no change, check once a year

1. Check if there is any change in IAM Specification
2. If YES, validate the IAM solution and all the relevant documents
3. Collect all the Proofs and update the date of control
4. If NO, directly collect all the Proofs and update the date of control"	"Retrieve the IAM matrix for the control and ressource plane 
Retrieve a screen shot of the IAM roles defined and used by the FT for the XaaS (Read-Create-Delete)
These items are formalized for the initial labelization. The RUN control is just a check for any update"	"The IAM solution is identified
The roles/scopes are defined
The IAM accesses are mendatory to reach the XaaS services"	Jaeger	"1. Automated report (script with IAMaaS integration)
2. Swagger describing Scopes/Roles (specify the IAM roles defined for the XaaS)"	In accordance with each feature team (and CSRO), as soon as a modification is realized about the IAM scopes/roles. If no change is realized, make a simple check once a year 	"Annual security committee with each CSRO : 
1. Any update on the XaaS wich could have an impact on the scopes/roles used ?
2. Dedicated documentation updated (Use of IAMaaS and the IAM matrix) ?"	The IAM socpe could be checked through the swagger	If there is no change about the IAM specifications, just check if the documentation have been updated (check to be realized once a year if during the months no change have been identified)	XaaS documentation about the IAM rules, reviewed by the CSRO at least once a year, at the anniversary date of labellization	"This control can be carried out by the Feature Team independently. 
If changes are made to the IAM scope (added or deleted roles) an update must be performed and validated by the CSRO. If no changes are made during the year, a simple check of the previous status will be carried out by the CSRO on the basis of the elements provided by the FT"	" - Check the configuration files about the use of IAMaaS :
    -tokenUrl: ""https://iamaas.int.world.socgen/iamaas/oauth2/access_token""
    -authorizationUrl: ""https://iamaas.int.world.socgen/iamaas/oauth2/authorize""
    -scopes : See the detailled scopes and the relevance in regards of the XaaS services and accesses requirements 
    -x-tokenInfoFunc: ""flask_iamaas_connexion.flask_iamaas_connexion.token_check"""	 - % of accounts that use IAMaaS 	"Yes
If non-compliance is identified, a recheck is needed to ensure that all the accounts (or type of accounts) use IAMaaS"
2	13	X0	Logs protection	"Control plane
Ressource plane
Ensure that the logs for both are properly secured"		Logs must be protected against unauthorized modifications and access.	"Check that the system logs are produced, using a suitable protection mechanism
Check that the local rights on the assets are strict (no modification other than by the owner of the file)"	"Identifiy the activites that need to be logged :
 - Activity logs, that shall be sent to the platform Metrology service or Log4all
 - System logs (syslog), that shall be sent to the SOC

1. Check if there is any change in scope of Logs protection
2. If YES, validate the control process and log protection mechanisms
3. Collect proofs and update the documents, and the date of the control
4. If NO, directly collect proofs and update the documents,and the date of the control"	Identify all the type of logs and the associated ways to share and protect them (at rest and in transit)	" - send the logs in a secure way to a secured aggregator. The logs cannot be accessed and modified by any user or administrator
 - store the logs locally but restrict access to Read Only for FT admin accounts (they must not be able to modify log files)"	"Fluentd
Metrology
Log4all
Ansible"	"1. Source code extract or screen shot or configuration extract (/home/XXX/logs) that show how the logs are realized, how and where they sent, and how they're protected regarding the requirement 
2. For local logs : Extract of the access rights (RW) 
3. Same thing for the syslog / aggregator
1. Automated report (script with IAMaaS integration)
2. Swagger describing Scopes/Roles (specify the IAM roles defined for the XaaS)
4. Swagger describing logs strategy for the XaaS"	"In accordance with each feature team (and CSRO), as soon as a modification is realized about the actions/perimeter whose it is relevant to log activities. Same thing about the rules of protection of the logs (local and those sent to aggregator).
If no change is realized, make a simple check once a year "	"Annual security committee with each CSRO : 
1. Any update on the XaaS wich could have an impact on the logs protection mechanism ?
2. Dedicated documentation updated (Protection mechanisms and destination) ?"	"Fluentd
Metrology
The log strategy could be checked through the swagger"	"If there is no change about the log protection specifications, just check if the documentation have been updated (check to be realized once a year if during the months no change have been identified)

Check with the FT if the log are still sent (sources are UP)"	"XaaS documentation about the log protection rules, reviewed by the CSRO at least once a year, at the anniversary date of labellization 
It may contain :
 - List of assets and their specificities
 - List of logs
 - Details of configuration ofr the log sending, and the encryption protocol used"	If it does not exist, it could be helpfull to check the dedicated documentation explaining how the logs are protected through the entire chain	" - Check the source code extract or screen shot or configuration extract 
 - Check the configuration for local logs (access rights), same thing for the syslog / aggregator
 - Check the configuration extract from Metrology or Log4all 
 - Check with the SOC team the good send of the logs"	 - % of type of logs that are properly sent and protected	"Yes
If non-compliance is identified, a recheck is needed to ensure that all the logs are are properly protected"
2	14	X0	Security incident management	"Control plane
Ressource plane
Ensure that the security incidents are identified and treated"		Security incidents management process documented, implemented and tested.	Check if the details about the security incident process is formalized for each XaaS, and applied by the FT :	"1. Check if a process is formalized (Global GTS process and dedicated process for each XaaS ?)
 - Contact information (who/what/how/when)
 - Monitoring tool link
 - Alerting scenarios implemented, way of communication, mitigation follow up with SOC team
2. Check if all the details about the incident qualification and mitigation are defined (Tresholds, levels of criticity, stakeholders, control tower process, SOC supervision, reporting and alerting, …) and applied by the FT
 - check by sampling how security incidents have been handled since the last RUN (Check in particular with Impulse & EE content)"	Ensure that all the FT work with the Incident treatment priority matrix. All the kind of scenarios / incidents for each XaaS must present this matrix to help the operationnal teams (SOC and others) to handle with efficiency the different incidents	" - The security incident process is defined, documented, tested 
 - All the ressources are supervised by the dedicated tool(s) and covered by the SIEM
 - All the requirements about the logs mgmt are already compliant and validated
 - a dedicated process for informing customers of the service is formalized "	"Grafana
JIRA"	"1. Incident management process 
2. incident prioritization matrix
3. If the process don't detail the communication to customers in the event of a security incident, a dedicated document must be formalized
4. If security incidents has already happened highlight that the process has been followed (screenshots, emails, Jira card)
5. Regarding the previous point, a capitalization must be defined within the process to improve the dedicated activities (within the incident report)"	"In accordance with each feature team (and CSRO), as soon as a modification is realized about the actions/perimeter whose it is relevant to log activities.
If no change is realized, make a simple check once a year "	"Annual security committee with each CSRO : 
1. Any update on the XaaS wich could have an impact on the incident mgmt process ?
2. Dedicated documentation updated ?"		"Check the platform documentation/Labelization report
Check the proofs for all requirements
Report and sharing contents
Mitigation plan defined by the CSRO + FT if any non compliance is identified
Recheck"	" - Incident management process formalized, relevant with the XaaS services, validated by the CSRO and shared with OPM
 - XaaS SLA
 - Incident prioritization matrix"	See how the incident mgmt process could be improved (see the dedicated point with CSRO community)	" - Check if the process is formalized and relevant (GTS or dedicated ?)
 - CHeck if the incident prioritization matrix is defined
 - Check if the details about the communication to customers in the event of a security incident is formalized"	" - % of assets covered by the incident security process
 - % of assets covered by the SOC
 - Process defined and tested"	"Yes
If non-compliance is identified, a recheck is needed to ensure that all the assets are covered and the communication process to the customers is defined"
3	15	X0	Outsourcing Communication	"Control plane
Ressource plane
Ensure for both that the activities of an external entity involved in the mgmt of the service are identified and monitored"		If an external entity is involved in the management of the XaaS or one of his ressource, ensure that these activities are identified and monitored, and that the customers (and other stakeholders) are informed of that	"Ensure that no modifications has made about the outsourced development or exploitation tasks, same thing about an external entity managing the service

If a FT has suscribed a maintenance contract with an external service provider, the RAMOS process must be followed to allow all the involved activities"	"1. Check if there is any change about the outsourced activities 
2. If YES, check if it involve one or several activities, and check the list of these activities, the list of associated assests (architecture, ressources, …), and validate them (CSRO), with a dedicated process
3. Valid the list updated by the FT and RAMOS informations
4. Update the date of the control
5. If NO, directly update te date of the control
"	" - Check the XaaS/FT activities, and check if all of them are realized by the FT or another one in SG
 - If on of these activities is outsourced, refer to RAMOS process "	" - All the activities outsourced are identified and managed by the CSRO
 - All the assets involved in the outsourced activities are identified and managed by the CSRO (risk vision in particular)
- The list is validated (CSRO) and updated"	"JIRA
RAMOS"	"1. For any change, check the reviewed inventory of all components 
2. For any change, check the form of the table with 3 columns “component name, outsourced, RAMOS-ID”
3. For any change, the column “outsourced” must specify if it's an outsourced component or remote admin (and any useful comment); or “NO EXTERNAL COMPONENTS detected” if applicable
4. If there is no change, update the list"	"In accordance with each feature team (and CSRO), as soon as a modification is realized about the outsourced acctivities/assets 
If no modification, once a year"	"Annual security committee with each CSRO : 
1. Any update on the XaaS wich could have an impact on the outsourced activities mgmt ?
2. Dedicated documentation updated ?"		"Check if one or several activities are outsourced
If yes, the FT update the list of these activities/assets, and then the CSRO validate it
If there is no change, a simple check is realized by CSRO"	Validated list of outsourced activities/assets by the CSRO		" - Check if it was reviewed and updated the inventory of all components 
 - If Yes, check if in case of outsourced activities, the form of the table with 3 columns “component name, outsourced, RAMOS-ID” is completed
 - If Yes, check if the column “outsourced” specify if it's an outsourced component or remote service suscribed (and any useful comment); or “,o external component or service detected” if relevant
 - If No, just update the list and the control date"	" - % of outsourced activities managed
 - % of outsourced assets managed"	No
3	16	X0	Provider security requirements	"Control plane
Ressource plane
Ensure for both that the external provider is compliant with SG security standard, for the realization of the outsourced activities"		Ensure XaaS follows SG outsourced compliance framework	"Ensure that the provider security requirements has not changed, at least once a year. If any change is realized for this item, a new labelization must be realized
"	"1. Check if one or several activities are outsourced
2. Check for each of them if the RAMOS-ID is completed and updated
3. If YES, validate the Activities list and RAMOS Information
4. Validate the documents and update the date of control
5. If NO, directly validate the documents and update the date of control"	Be acquainted with RAMOS	" - All RAMOS-ID are completed for the list of outsourced activities
 - All the proofs are availables within JIRA"	"JIRA
RAMOS"	"1. Check if the LABELIZATION PROOFS within JIRA are still relevant since the last labelization/control
2. In case of outsourced activities, check the form of the table with 3 columns “component name, outsourced, RAMOS-ID”
3. The column “outsourced” must specify if it's an outsourced component or remote admin (and any useful comment); or “NO EXTERNAL COMPONENTS detected” if applicable"	"In accordance with each feature team (and CSRO), as soon as a modification is realized about the outsourced acctivities/assets 
If no modification, once a year"	"Annual security committee with each stakeholders : 
1. Any update on the XaaS wich could have an impact on the outsourced activities mgmt ?
2. Dedicated documentation updated ?"	Ramos completion	"Check if one or several activities are outsourced
If yes, check the list of these activities/assets and the FT justifications"	Validated list of outsourced activities/assets by the CSRO		"Checks realized by CSRO :
 - Check if it was reviewed the inventory of all components and challenged outsourced components if relevant
 - Check if in case of outsourced activities, the form of the table with 3 columns “component name, outsourced, RAMOS-ID” is completed
 - Check if the column “outsourced” specify if it's an outsourced component or remote service suscribed (and any useful comment); or “,o external component or service detected” if relevant"	" - % of outsourced activities managed
 - % of outsourced assets managed"	"No
Based on the documents completed by the FT initialy, and checked by G3C team"
3	17	X0	Compliance review	"Ressource plane
Ensure this one is compliant with regulatory requirements"		Ensure XaaS complies with both GDPR and ASA requirements	"Check if the GDPR compliance is still applied for the XaaS services
Check if any change has made for the XaaS during year"	"1. Check if the PO have identified all the kind of datas handled by the XaaS (email, @email, names, userID, …)
2. Check if the compliance officer have delivered his GDPR validation
3. Check if there is any change for these items
4. If YES, validate the change and compliance report
5. Validate the documents and update the date of control
6. If NO, directly validate the documents and update the date of control"	Communication with the compliance officer	"GDPR :
 - Personal data are identified and listed
 - Compliance officer validated the GDPR assessment
 - Proof are updated on JIRA
ASA :
 - Compliance officer validated the ASA
 - Proof are updated on JIRA"	"ASA
JIRA"	"1. Compliance officer validation for GDPR and ASA requirements
2. Proofs and JIRA card updated by the CSRO"	"In accordance with each feature team (and CSRO), as soon as a modification is realized about the kind of datas handled by the XaaS (drived by the applicable regulatory)
If no modification, once a year"	"Annual security committee with each CSRO : 
1. Any update on the XaaS wich could have an impact on the data handled and the associated regulatory ?
2. Validation realized by the compliance officer ?
3. Dedicated documentation updated ?"	GDPR review workflow	"Check if any data is impacted by the GDPR compliance, and if any change has been made during the year
If yes for the first one, update the control date
If yes for the second one, the compliance officer will validate the update"	Validation of the compliance officer (XaaS concerned or not by GDPR requirements). 		"Checks realized by CSRO :
 - Check if there is any evolution of the XaaS context regarding the GDPR requirements (if not, this check is to be realized once a year)
 - Check if the validation of the compliance officer for GDPR and ASA requirements is still applicable "	" - % of compliance with GDPR requirements
 - % of residual risks validated and managed (ARA) "	Yes as soon as the mitigation plan is applied
3	18	X0	Obsolescence management	"Control plane
Ressource plane
Ensure for both that the obscolesence mgmt is defined for all involved components"	"7. dependancies
(see the control #1)"	Obsolescence management process is defined by the FT and XaaS for components near of End-Of-Life (not longer supported), or other components (opensource) that could be deprecated	"Maintain the list of component involved by obsolescence

Use Safety (dependencies) within the CI/CD pipeline in blocking mode "	"The FT must formalize a list of all components,and realize a continuous monitoring to ensure that no one of them could be deprecated in the near future, which could have an impact on XaaS

Run Safety : Think to writte the code dependencies within the dedicated file : safety check -r requirements.txt
https://github.com/pyupio/safety/blob/master/README.md
This scan is automated and run daily

Safety :
1. Validate the weekly scan results and mitigation plan
2. Follow-up of the mitigation plan
3. Update the date of the control

Obsolescence of components :
1. Check if there is any change about the component involved by obsolesence
2. If YES, valid the updated list (edited by the FT)
3. Update the date of the control
4. If NO, realize the action #3"	"Safety : 
Ensure that the message error when the scan is KO is well defined
Ensure that the generic remediation plan is defiened
Ensure that the scoring CVSS is defined for each kind of vulnerability"	" - Obsolescence mgmt process is still defined
 - List of XaaS component impacted by this process (dependencies, …) is still formalized
 - Release notes are still available 
 - Scan (Safety) for each container with dependencies is daily realized (vulnerabilities and remediation plan are automaticaly produced)"	"Safety
JIRA"	"1. Obsolescence mgmt process is not modified 
2. Updated list of XaaS component impacted by this process (dependencies, …)
3. The release notes with end of life details are still formalized
4. Scan results (Safety) for each container with dependencies (see control#1)
 5. Pipfile (package dependency management), so imports requirements.txt type files into Pipfile"	"The FT shall realize monitoring activities about the obsolesence of the involved XaaS assets, and for any modification shall update the dedicated list and share it with the CSRO (for any component identified as being at end of life). 
Check once a year  if there is any change about the component involved by obsolesence

Daily scans are realized with Sofasec (Safety) to assess the dependencies vulnerabilities. THe results are sent to Analytics, and a weekly meeting is realized involving FT and CSRO to analyze theses results, and define the mitigation plan"	"Weekly security committee with each CSRO : 
1. Is the coverage rate 100% compared to SGithub's repositories ?
3. Are there untreated vulnerabilities ?

The results of SOFASEC scans will be exported to Analytics. These results must be checked weeckly by the CSRO, the PO and the SM , especialy regarding the high and very high vulnerabilities levels.this implies an acknowledgement by the feature team

Annual commitee to discuss about the use of obscolete components"	"Dedicated tool (realization), for Safety 
-> SoFaSec
Eagle eye (Mgmt of the risks and vulnerabilities)
Analytics security (for a global overview of the security KPI)"	"Installtechnical environment 
Scan realization
Report and sharing contents
Mitigation plan defined by the automation of the result writting and shared with CSRO + FT
Monitoring of the mitigation plan
Recheck"	"• List of asset monitored regarding their possibly obscolescence
•	Weekly Report on Safety usage to FT/CSRO: %Repositories scanned per FT (report available)
• Number of vulnerabilities founded for each repo (and total)
• Assess there is no skip or Nosec in the scan results
• Verify that vulnerabilities have been addressed 
•	Daily report to FT/CSRO on safety findings per FT : # findings per repo and FT 
•	Qualify and communicate (automation through Sofasec) to CSRO Safety findings details : 100% findings analyzed and corrected"	"Curently, Sofasec is ran every day, and produce raw results, shared within Analytics
Tomorrow, the Sofasec scripts will be improved (refine commands for a coverage and relevance increased, filter certain results, …), same things for a proposal of mitigation plan for each kind of vulnerability identified. Results will be shared with analytics, with a view for vulnerabilities (and other Sofasec KPI) and another one for the mitigation plan. The scoring CVSS will be also integrated to the results, to help the FT to prioritise the mitigation plan

Sofasec scan will still be ran every day.
For each major new release, GSC team will use Sofasec and realize a further analyze of results (false-positives, ...), but it will be realized within a new labelization context"	" - Check if the obsolescence mgmt process is still applicable
 - Check if the list of XaaS component impacted by this process (dependencies, …) is defined
 - Check the release notes with end of life details
 - Check weekly the scan results (Safety) for each container with dependencies (see control#1)
 - Same thing about Pipfile (package dependency management), so imports requirements.txt type files into Pipfile"	 - % of components identified as being at end of life and managed	"Yes (automated with Sofasec)
No for the components obsolescence"
1	19	X0	Vulnerability assessment	"All assets
Assess if several vulnerabilities impact the assets deployed on the FT XaaS"		"Realize a vulnerability assessment and a remediation plan for each asset within a XaaS (VM, API, ...)

Each stakeholder must fix vulnerabilities on its side according to Shared Responsibility Model

The FT must remove vulnerable images and rebuild new ones as soon as an alert bulletin from FT Orchestrated containers is sent"	" Check if Qualys agent is already installed on all the the assets within the XaaS, to automatically run the scans
Check if other assets are used, for which the agent cannot be installed (realize a manual scan)
Check if certain components have been audited (Pentest), and if the mitigation plan is closed
Check if the FT have suscribed to an external service provider activities (monitoring, security patching, ...) 
"	"Identify with the FT all assets deployed within the XaaS (list defined and maintained by himself)

The Qualys scan is automated and run daily

 Use the dedicated tool to the reporting

Weekly check :
1. Weekly Qualys Scan result check
2. Add comments, formalize specific requests to FT
3. Validate the weekly scan results and mitigation plan
4. Mitigation plan follow-up (requirement #28)
5. Update the date of the control"	Cloud VM must be packaged with the Qualys agent. For virtual appliance (or any asset where Qualys agent cannot be installed), vulnerability assessment must be performed manually	" - Scan (Qualys) for each asset is daily realized
 - The vulnerability report is automaticaly produced with Qualys (Daily), and if some vulnerabilities are found, FT produce a remediation plan (mean life of VM per FT or XaaS, vulnerabilities per severity - 1 -> 5 - )
he FT is committed to fix all level 4 and 5 vulnerabilities by rebuilding VM as needed."	"Qualys
Sec Qualys (reporting)
Analytics
Eagle Eye"	"1. Up to date list of assets on the XaaS
2. Scan report (mean life of VM per FT or XaaS, vulnerabilities per severity - 1 -> 5 - )
3. Mitigation plan"	Daily, with an automated process based on Qualys and associated scripts, to run scan and export results to Analytics, and a weekly meeting is realized involving FT and CSRO to analyze theses results, and define the mitigation plan	"Weekly security committee with each CSRO : 
1. Number of vulnerabilities founded for each XaaS
2. Severity of vulnerabilities
3. % of conformity (and history)
4. Are there untreated vulnerabilities ?

The results of Qualys scans will be exported to Analytics. These results must be checked weeckly by the CSRO, the PO and the SM , especialy regarding the high and very high vulnerabilities levels.this implies an acknowledgement by the feature team
"	"Dashboard (analytics security)
Dedicated tool (SecQualys)
Puppet (for the hardening)"	"Set the schedule of automated scans for qualys (and manual scans if relevant)
Run scans
Analyze reports
Share with involved FT
Follow up the mitigation plan produced by the FT"	"•	Weekly report on OS vulnerabilities to FT/CSRO : compliance rate, #vuln… (report available)
•	Follow up of the remediation with the CSRO and FT to ensure that patch management is done continuously : All actions of the remediation plan must be validated and documented
•	Support FT to fix vulnerabilities (with the CSRO in charge of the FT) : 75% compliance rate objective"	"Include the CVSS scoring for the vulnerability scans
The CVSS is still ofered by Qualys, so it is an easy way of improvement"	" - XaaS components must be listed by FT
List all assets involved in the XaaS services. It could be crossed with a golden source (Marley) to double check these list
 - XaaS components versions  
Check the version of the XaaS components (OS ...)
 - Qualys scans are performed daily, and the results are validated by the CSRO.
Ensure that the scope of QUalys scans is relevant. 
 - Qualys reports are sent to Analytics for reporting and alerting when vulnerabilities are detected
Ensure that every reports are sent to Analytics and available for the FT/PO/SM
 - No vulnerabilities have been identified at date (CSRO validation) / or / X vulnearbilities have been identified : See the dedicated action plan 
Ensure that a false-positive results have been assessed by a dedicated process (to send to the CSRO and the FT only the relevant results)
 - A dedicated process must be defined to apply the mitigation plan
Ensure that a dedicated process is defiened by the FT, covering all the scope of the XaaS.
This process must specify how the mitigation plan (and when) could be applied on the XaaS scope (compliant with the SVM standard and associated SLA), if a monthly reconstruction (of the VM) is planed (So check the OS versions that must be Up2date -> Software factory, to ensure that the mitigation plan is not applied to several VM whose OS is already deprecated) "	Use directly the KPIs from Qualys weekly repporting 	A recheck will be automaticaly realized trough the following scan
3	20	X0	Client data in non-prod environment	"Control plane
Ressource plane
Ensure thatt if there is customer data in non production environment, they protected againt dumping"		Explicit approval for client data used in non-production environment	"Check if the FT use customer data in development environment
If yes a formal approval must be gathered from all stakeholders"	"Check if any change has made about the use of production data on the development environment (The initial status doesn't have to change : If the XaaS require customer/production data for experimentation/testing (Dev/Pre-prod), the PO must validate this point, to ensure that no risk is identified with this kind of activities on non-prod environment
If any change is identified, check the justification formalized by the FT, and the approval made by the PO
If there is no change during the year, realize a quick check once a year

1. Check if XaaS require client data in Non-Prod environment
2. If YES, check the official validation of PO and associated documents
3. Check for approval from stakeholders
4. Update the date of control
5. If NO, directly update the date of control
"	"Retrieve the jdata matrix with the valdiated environment of use

Retrieve the PO validation for these uses "	" - Justification made by the FT, and validated by the PO : No customer data are used in preprod environment
 - For another case, or any change of status, the justification must be documented by the FR, and valdiated by the PO ( Check official approval of the stakeholders for the use of customer data in development environment)"		"1. FT justification (change or data use documented)
2. message of stakeholders (validation of the PO)"	"In accordance with each feature team (and CSRO), as soon as a modification is realized about the non-prod environments, justifying the use of customer/production datas.
If there is no change identified, once a year"	"Annual security committee with each CSRO : 
1. Any update on the XaaS wich could have an impact on the non-prod environments (use of prod datas) ?"		"Has there been a change in the use of the data environment?
Yes : FT must justify this change, and the PO must validate it
No : Realize a quick check (element already assessed during the previuous labelization review) and update the control date and conclusions"	"Validation of the FT and CSRO that this requirement is not applicable as the team does not require customer data for testing in non-production environment.

If yes, the PO validation is needed (official msg)"		"Check if the XaaS require customer/production data for experimentation/testing (Dev/Pre-prod).
If yes, collect the official validation of the PO for the use of prod datas on the non-pod environments"	 - % of production data on non production environment alllowed by the product owner	No
3	21	X0	Environment segregation	"Control plane
Ressource plane
Assess if there is an environment segregation for both"		Segregation between XaaS environments (network and access control segregation) must be applied	"Check if the segregation between environments is applied
Check if dedicated ID are used to access to each environment"	"If any change has been made on segregation, identify them with the updated documentation provided by the FT
Then check the architrecture details, and check if any communication could be realized directly, avoiding the FW beetween them 
Check if dedicated domain accounts are used to conect to each environments

1. Check if there is any change in Environment segregation & account IDs
2. If YES, validate the environment segregation and account ID's
3. Collect and validate the docs/proofs and update the date of control
4. If NO, directly collect and validate the docs/proofs and update the date of control"	"Ensure with the FT that there is no change made about the environment segregation within the XaaS
If any change is made, realize the checks detailled for the control activities"	"The communication are checked, no interaction between environments
ID are checked, a dedicated one is used to connect to each environment
Documentation is updated"	Ansible	"1. Architecture scheme showing the lack of interaction between environments (details of subnets, IP addresses plan, ...)
2. ACL extract from the front FW of each environement (associated with the details of the architecture scheme, it must detailled that there is no dependencies or traffic between them)
3. Extract of accounts used for each environment (for each of them, the accounts must be dedicated for each environment, and be nominative for each dev "	"In accordance with each feature team (and CSRO), as soon as a modification is realized about the environments seggregation of the platform 
If no modification, once a year"	"Mensual security committee with each CSRO : 
1. Any update on the XaaS wich could have an impact on the environments seggregation ?
2. Any update of the ID for each environment ?
3. Dedicated documentation updated ?"		Same thing than the control activities	"
Report to FT/CSRO on findings per FT : Documentation, configuration, ID compliance "		"If any change has been made on segragation, identify them with the updated documentation provided by the FT
Then check the architrecture details, and check if any communication could be realized directly, avoiding the FW beetween them 
Check if dedicated domain accounts are used to conect to each environments"	" - % of environments seggregated
 - % of ACL compliant to apply this seggregation
 - % of dedicated ID used to each environment "	No
	22	X0	SSA ZONE	Not applicable																	
3	23	X0	Security awareness training	All FT members	1. Security awareness	FT’s developers and security team members must particip to hands-on security sessions	Check the content of the awareness toolkit to ensure that is efficient regarding the needs and the purposes of the hands on sessions and  peoples involved	"1. Monthly, check the participation of FT members to each hands on session
1.1. If YES, update the date of the control
1.2. If NO, check the participation of FT members for the monthly hands on sessions and plan the next sessions
2. Grab the feedback and comments in order to improve the realisation of the hands on sessions
3. Analyze the feedback and work with G3C to improve the hands on content / form
4. Update the date of the control
5. Once a year, validate the awareness toolkit, then update the date of the control"	"Define with G3C and mgmt the baseline of the awareness hands on to ensure that the content is in coerence with the needs for FT members

Check the subject of the awareness sessions (“Security Audit” and “Code Security” hands-on sessions)
Check if all the FT members have done this awareness session (once a year)
Check if all the security team members have done this awareness (or dedicated awareness session) session once a year
Check the dates of the last and next session, and the participation of people "	"The participation of all team members is checked
The list of participants is checked"		"Date of session
list of participants with their signature"	Once a year for the awareness campaigns for each people involved 	"Mensual security commitee with each CSRO :
1. Did the FT and SEC members who were to participate to the hands on sessions do so well?
2. What is the planification of next session? Subject ? Purpose ?
3. The feedback of the last session 

Annual security commitee with each CSRO :
1. The content of the hands on sessions for all the following year"		"1. Monthly, check the participation of FT members to each hands on session
1.1. If YES, update the date of the control
1.2. If NO, check the participation of FT members for the monthly hands on sessions and plan the next sessions
2. Grab the feedback and comments in order to improve the realisation of the hands on sessions
3. Analyze the feedback and work with G3C to improve the hands on content / form
4. Update the date of the control
5. Once a year, validate the awareness toolkit, then update the date of the control"	"The number of participants for each hands on session
The participation follow up for the involved peaoples (FT and SEC teams members)
The feedback and the mitigation plan developped by G3C to improve the content/methodology for the following sessions"	Always realize hands on session which deal with subjects of current interest to the teams, which deal with in-depth security topics, enabling everyone to learn things that can be applied operationally (e.g. avoid talking about the TOP10 OWASP to people who do not deal with vulnerabilities or Web applications)	"Evaluation of the Hands on sessions annual program
Follow-up of the participation of the hands on sessions, for each team member (FT, SEC, …)
Assessment of the feedbacks , and follow-up of the action plan to improve them"	"First view :  
 - The hands on sessions planning for the year is validated (G3C, FT and CSROs)
Second view :
 - % of FT members who attended a hands on session"	No
3	24	X0	Shared responsibility model	"Control plane
Ressource plane
Ensure that a shared responsibility model is definied for both"		Definition of stakeholders roles and responsibilities must be done	Ensure that the SRM defined for the service is compliant with the SRM matrix defined by the MGMT	"1. Check if there is any change in SRM Model
2. If YES, validate the change in SRM model and RACI
3. Update the date of control
4. If NO, just update the date of the control"	Check the RACI defiened (shared responsibility model) for each activities involved in the XaaS processes (Patch mgmt, mitigation plan implementation, …)	The shared responsibility model is checked and validated. Each activity is detailled and an associated owner is specified		RACI, SRM process	Once a year if tere is no modification	"Annual security committee with each CSRO : 
Is any change in SRM Model ?"		"1. Check if there is any change in SRM Model
2. If YES, validate the change in SRM model and RACI
3. Update the date of control
4. If NO, just update the date of the control"	"Governance matrix.
For each activity (Build, RUN), it must be specified a RACI
For example, for the patch mgmt, who analyze the vulnerability, his gravity, the associated patch, the opportunity to patch, the impact on business and security if the patch is applied (or not), and who apply the patch (and who will carry out the arbitration if the decision is not validated by all stakeholders)"			 - Is the shared responsibility model defined, validated and applied ? Y/N	No
3	25	X1	Data transfert encryption	"Control plane
Ressource plane
For both, ensure that all communications between XaaS and customer are cyphered"		Data in transit concerning the API must be cyphered (cypher suite compliant with SG standard)	Ensure that all the data transfert encryption mechanisms are defined and applied, and the associated documentation is formalized	"1. Check if there is any change in data transfert encryption model
2. If YES, validate the change of data transfert encryption model
3. Check if the the new model is applied by the FT, and the documentation is updated 
4. Collect and update proofs and documents
5. Update the date of control
6. If NO, realize the actions #4 and 5 "	Check the SG requirements about the data transfert encryption	TLS Labs scan ran on the XaaS (highlighting potential encryption algorithms not allowed by the GTS encryption policy, or deprecated versions - TLS1.0, ...)		TLS Labs scan report	Once a year if tere is no modification	"Annual security committee with each CSRO : 
Is any change in data transfert encryption model"		"1. Check if there is any change in data transfert encryption model
2. If YES, validate the change of data transfert encryption model
3. Check if the the new model is applied by the FT, and the documentation is updated 
4. Collect and update proofs and documents
5. Update the date of control
6. If NO, realize the actions #4 and 5 "	"List of protocols used, and cyphers
Associated documentation"			"
First view :  
 - % of communications cyphered
Second view :
 - % of communications for which encryption complies with SG standards"	No
3	26	X1	Exploitation documentation	"Control plane
Ressource plane
Ensure that an exploitation documentation is formalized for both"		Publish an up2date XaaS administrator guide documentation	Ensure that all the exploitation documentation is formalized, applied by the FT members, and up2date	"1. Check if there is any change in Exploitation Documentation
2. Validate the Exploitation document
3. Update the date of control"	Check the evolutions of the documentation since the labelization phase, and each iteration of the documentation modifications	"All exploitation actions are centralized on a single document (there must be no links to other documents)
The exploitation doc is stored on a secured repository"		"1. Admin guide URL (even if not publicly available)
2. CSRO report he verified the admin guide(s)"	Once a year if tere is no modification	"Annual security committee with each CSRO : 
Is any change in Exploitation Documentation ?"		"1. Check if there is any change in Exploitation Documentation
2. Validate the Exploitation document
3. Update the date of control"	"Exploitation documents
Operationnal and user visions described within the procedure"			 - First view : Exploitation documentation updated 	No
3	27	X1	Log centralization	"Control plane
Ressource plane
Ensure that the logs are forwarded with appropriate tool for both"		XaaS must push their logs into a centralized data collector.	Ensure that all the logs defined for the platform are identified, and sent seucrely to a centralized solution (Log concentrator as Metrology for exemple)	"Check if the activity logs (API) was sent to the platform Metrology service
Check if the system logs (syslog) was sent to the SOC
Check the platform technical exception (frontend and backend hosts logs, Openstack component, …)

1. Check if there is any change about the centralized Logs collectors
2. If YES, validate the control process and log centralization mechanisms
3. Collect proofs and update the documents
4. If NO, directly collect proofs and update the documents"	"Check the control #13 to list the logs that shall be produced by the XaaS
Identify the solution used as a log concentrator"	All logs are collected to a central collector and the protection mechanisms are assessed and validated	"Metrology
LOG4ALL
Ansible"	"1. Extract of list of log sent to a central collector (Metrology, SOC, …)
2. SS of the details of the logs (KIBANA, …)"	Once a year if tere is no modification	"Annual security committee with each CSRO : 
Is any change about the centralized Logs collectors ?"		"Check if the activity logs (API) was sent to the platform Metrology service
Check if the system logs (syslog) was sent to the SOC
Check the platform technical exception (frontend and backend hosts logs, Openstack component, …)

1. Check if there is any change about the centralized Logs collectors
2. If YES, validate the control process and log centralization mechanisms
3. Collect proofs and update the documents
4. If NO, directly collect proofs and update the documents"	"List of events/actions that generate a log
Logs details (form, content, mechanismes of storage and sending, …)"			 - First view : % of logs sent to a dedicated log concentrator	No
1	28	X1	Vulnerability mitigation plan	"All assets :
Follow up the mitigation plan from scan vulnerabilities, source code audit, risk analysis, pentest, CERT/SOC alert, incident, ...)"		Formalize a mitigation plan for each identified vulnerability and associated risk	"See the control #19 for the vulnerability scan
See the controls #1, 5, 6, 18 for source code audit

Follow up the remediation plan for the pentest (Analytics)
Follow up the remediation plan for the automated scans (SOFASEC) (Analytics)
Follow up the remediation plan for the Qualys scans (Analytics)
Follow up the remediation plan for the risk analysis (Eagle Eye)
Follow up the remediation plan for the SOC/CERT alerts, or incident management process (if relevant)"	"Identify all the vulnerabilities and follow the remediation plan :
 > SecQualys for vulnerability scan
 > Eagle eye for risk analysis
 > Automatic report for Sofasec
 > Results of audits realization (G3C, outsourced, ...)
 > Global dashboard (analytics security)
1. Validate the weekly scan results and mitigation plan follow-up
2. Validate the findings and the dedicated mitigation plans (for each new occurence - ARA update, new audit report, SOC report, incident magmt report -)
3. Validate the documentation and update the date of control"	"Ensure that the dedicated procedure is formalized
Check if the team Wiki contains a flaw remediation procedure. This procedure shall describes how to handle any detected vulnerability, whatever the source, and how to communicate with customers if necessary
The mitigation plan follow-up include that the previous occurence are still monitored, until that all the mitigations plans are deployed, all the associated actions are closed"	"The vulnerability management process is formalized and available within the FT wiki 
The dedicated procdure is formalized and used by the stakeholders
Differents reports and associated mitigation plans are available
The global annual check allow to ensure that all these elements are coherents, known by the stakeholders and applied"		"1. FT Wiki (process and procedure)
2. Reports (Representative sampling -> Pentest report, Sofasec and Qualys reports, …)
3. Associated mitigation plans  
4. Mitigation plan follow up"	"Weekly for the follow-up of the mitigation plans for automated scans (Sofasec, Qualys)
As soon as a new occurrence appear (Pentest, ARA modification, SOC/CERT notification, …)
The both kinds of follow-up imply that they must be managed until that all the actions of the mitigation plan are all closed"	"Annual security committee with each CSRO : 
1. Check of the weekly scan results and mitigation plan follow-up
2. Assessment of the rules used to perform the scans, and identify the ways of improvement"		"Identify all the vulnerabilities and follow the remediation plan :
 > SecQualys for vulnerability scan
 > Eagle eye for risk analysis
 > Automatic report for Sofasec
 > Results of audits realization (G3C, outsourced, ...)
 > Global dashboard (analytics security)
1. Validate the weekly scan results and mitigation plan follow-up
2. Validate the findings and the dedicated mitigation plans (for each new occurence - ARA update, new audit report, SOC report, incident magmt report -)
3. Validate the documentation and update the date of control"	"•	Align remediation actions identified on ARAs and JIRA cards, all remediation must have a JIRA card
•	Review and assign JIRA card to the right owner, with the CSRO sponsoring. All the JIRA remediation card must be assigned and validated with the product owner
•	Ensure that all items are scheduled (ETA, linked in FT backlog) and closed eventually
•	Monthly report on open remediation actions per FT to the FT and CSRO 
•	Checks ARA remediations plan error (improve exiting tooling)"	"Communication with all stakeholders and monitoring of the progress of the FT activities needs to be clarified

Currently, the governance not allow a well application of the mitigation plan, by the good actors, within the required timeframe"		" - First view : % of actions of the mitigation plan closed (grab informations about all the open mitigations plans)
 - Second view : % of actions planned for the next PIs
 - Third view : % of actions that cannot be implemented (regardless of the issue)"	No
	29	X1	Dataflow filtering	"Control plane
Ressource plane
For both, ensure that all assets are properly filtered network wise"		Filter flows concerning the XaaS (micro-segmentation)	"List the filtering capabilities within the XaaS (SSA Zone, Openstack, AVI controller, …)
List the rules that must be applied within ACL for each XaaS
Compliance report with the SG network filtering policies"	"1. Check if there is any change in Dataflow filtering
2. If YES, validate the Micro-segmentation
3. Check if the micro-segmentation is appliyed for each component of the XaaS (no current derogation)? 
3.1 If YES, update the documentation and assess the compliance with SG network filtering policies
3.2 If NO, realize a micro-segmentation implementation follow-up (and derogations closing), and then return to the step #2
4. Collect and update proofs and documents
5. Update the date of control
6. If NO, realize the actions #4 and 5 "	"Check the list of all assets of the XaaS, and the architecture documentation, to ensure that all the filtering rules are applied within the XaaS
Check if there is yet some derogations about the micro-sgmentation within XaaS"	"Filtering solution is deployed for the relevant scope
ACL are definied in compliance with the SG policies and the relevant scope for each XaaS
These elements are documented and must be validated by the CSRO 
If there is some derogations, they documented and must be valdiated by the validated"		"Architecture details (Filtering and dataflow matrix)
Network policy for the XaaS
Extract of the ACL for the relevant network filtering points"	"In accordance with each feature team (and CSRO), as soon as a change is realized for a dataflow filtering rules/mechanisms
If there is no change, once a year "	"Annual security committee with each CSRO : 
Is any change in Dataflow filtering ?"		"1. Check if there is any change in Dataflow filtering
2. If YES, validate the Micro-segmentation
3. Check if the micro-segmentation is appliyed for each component of the XaaS (no current derogation)? 
3.1 If YES, update the documentation and assess the compliance with SG network filtering policies
3.2 If NO, realize a micro-segmentation implementation follow-up (and derogations closing), and then return to the step #2
4. Collect and update proofs and documents
5. Update the date of control
6. If NO, realize the actions #4 and 5 "	Filtering and data flow matrix for each component deployed within the platform				No
	30	X1	Open source security and support	"Control plane
Ressource plane
For both, ensure that all used opensource components are maintened"		Open source components must be supported	Ensure that all the opensource components that used within the XaaS are still maintened and up2date	"1. Check if there is any change for Opensource components used on the platform
2. If YES, validate the modification and support provided for the involved component
3. Check if these components are properly maintened (active community or with an outsourced service provider). These informations must be evaluated and validated by the FT and CSRO
4. Check if the opensource components documentation that used within the XaaS is formalized, up2date 
5. If NO, validate the support provided for all the XaaS Opensource components and update the date of control
"	"Check the list of Opensource components that used for the XaaS, formalized by the FT. 
Check the type of active support provided by the community or by a dedicated service provider, and ensure that all involved components of the XaaS are covered by one of them."	"The opensource components documentation is formalized
The opensource support is validated by the CSRO"		List of opensource components validated by CSRO (with details about the maintain of them)	"In accordance with each feature team (and CSRO), as soon as a change is realized for an Opensource component in the XaaS. 
If there is no change, twice a year to be aware about the evolution of an opensource community"	"Annual security committee with each CSRO : 
Is any change about Opensource components used on the platform"		"1. Check if there is any change for Opensource components used on the platform
2. If YES, validate the modification and support provided for the involved component
3. Check if these components are properly maintened (active community or with an outsourced service provider). These informations must be evaluated and validated by the FT and CSRO
4. Check if the opensource components documentation that used within the XaaS is formalized, up2date 
5. If NO, validate the support provided for all the XaaS Opensource components and update the date of control
"	"List of opensources components used within the platform
Details about the comunity that maintain the involved components of the platform"				No
	31	X2	Code audit	"Control plane
Ressource plane
For both, ensure that a source code audit is realized by an external entity"	8. Code security check	External code audit must be realized for each major release (External entity : A second or third party audit is necessary => A SG audit team or an external service provider must realize these activities)	"NB : For this requirement, the external Pentest service provider could be replaced by G3C 
Check if an audit code have been provided for the last release (check the release versions)
The code audit have to be relalized for each new release (update of the labelization activities, follow the process). If there is no new release during last year, a source code audit must be realized at least once a year
It is important that  the external audit team does not use the same tools as the SEC teams, so that they can compare results using their own methods and tools
The relevant perimeter must be API code, Library, plugin or script (Third-party or its own development)"	"1. Analyze the source code audit report. Is the report validated ?
2. If YES, validate the source code audit report (and share the mitigation plan)
3. Mitigation plan follow up (Control #28)
4. Validation of the mitigation plan + Update the documents + date of control
5. If NO, source code audit report writting : Results and mitigation plan modified by the service provider
6. Then, realize the actions #3 and 4"	"Planification of the source code audit realization (Schedule : Source code audit for each new major release, or at least once a year). Identification of the source code audit service provider (As already mentioned, this activity could be realized by G3C)
Definition of the source code audit details/context (perimeter, purpose, prerequisites, access to the source code, accounts, IAM, ...)"	"Code audit has been executed by an external entity
A vulnerability mitigation plan has been established"		"Vulnerability mitigation plan regarding external code audit
Security code audit reports (initial and re-audit reports)"	"In accordance with each feature team (and CSRO), as soon as a major release is developed, a new labelization will be made. This audit will be realized once a year too, if there is no significant modification made on the XaaS source code
on recommendation (vulnerability to be patched, a component version to upgrade, ...)
->As soon as a new major relaease is edited for production
->If there is no new major relaease, at least once a year"	"Security committee with each CSRO : 
Is the  source code audit report validated ?
Is the mitigation plan is implemented ?"		"1. Analyze the source code audit report. Is the report validated ?
2. If YES, validate the source code audit report (and share the mitigation plan)
3. Mitigation plan follow up (Control #28)
4. Validation of the mitigation plan + Update the documents + date of control
5. If NO, source code audit report writting : Results and mitigation plan modified by the service provider
6. Then, realize the actions #3 and 4"	"Audit report that contains :
Vulnerability assessment
Risk assessment
Mitigation plan"			" - First view : Source code audit realized for the last major release, or at least once in the last year (Y/N)
 - Second view : Number of vulnerabilities
 - Third view : Number of vulnerabilities closed within the mitigation plan follow-up
 - Fourth view : Number of high and very high level vulnerabilities that are still open"	Yes
	32	X2	Security Audit (white box pentest)	"Control plane
Ressource plane
For both, ensure that a pentest is realized by an external entity"			"NB : For this requirement, the external Pentest service provider could be replaced by G3C 
Check if a pentest have been provided for each last releases (see the release versions)
Check if the audit report have been validated by the CSRO
Check if the associated mitigation plan have been formalized by the audit team, and if he is managed by the CSRO (any issue or action still opened), and if the FT have implemented the mitigation plan (mainly significant and major risks )"	"1. Analyze the Pentest report. Is the White box Pentest report validated ?
2. If YES, validate the Pentest report (and share the mitigation plan)
3. Mitigation plan follow up (Control #28)
4. Validation of the mitigation plan + Update the documents + date of control
5. If NO, Pentest report writting : Results and mitigation plan modified by the Pentest service provider
6. Then, realize the actions #3 and 4"	"Planification of the Pentest realization (Schedule : Pentest for each new major release, or at least once a year). Identification of the Pentest service provider (As already mentioned, this activity could be realized by G3C)
Definition of the Pentest details/context (perimeter, purpose, prerequisites, accounts, IAM, ...)"	"Pentest has been executed by an external entity
A vulnerability mitigation plan has been established"	"Analytics
EE"	"Vulnerability mitigation plan regarding external Pentest
Pentest reports (initial and re-audit reports)"	"In accordance with each feature team (and CSRO), as soon as a major release is developed, a new labelization will be made. This audit will be realized once a year too, if there is no significant modification made on the XaaS 
on recommendation (vulnerability to be patched, a component version to upgrade, ...)
->As soon as a new major relaease is edited for production
->If there is no new major relaease, at least once a year"	"Security committee with each CSRO : 
Is the black/grey box Pentest report validated ?
Is the mitigation plan is implemented ?"		"1. Analyze the Pentest report. Is the White box Pentest report validated ?
2. If YES, validate the Pentest report (and share the mitigation plan)
3. Mitigation plan follow up (Control #28)
4. Validation of the mitigation plan + Update the documents + date of control
5. If NO, Pentest report writting : Results and mitigation plan modified by the Pentest service provider
6. Then, realize the actions #3 and 4"	"Audit report that contains :
Vulnerability assessment
Risk assessment
Mitigation plan"			" - First view : Pentest realized for the last major release, or at least once in the last year (Y/N)
 - Second view : Number of vulnerabilities
 - Third view : Number of vulnerabilities closed within the mitigation plan follow-up
 - Fourth view : Number of high and very high level vulnerabilities that are still open"	Yes
	33	X2	Pentest (Blackbox / Greybox Pentest)	"Control plane
Ressource plane
For both, ensure that a pentest is realized by an external entity"			"NB : For this requirement, the external Pentest service provider could be replaced by G3C 
Check if a pentest have been provided for each last releases (see the release versions)
Check if the audit report have been validated by the CSRO
Check if the associated mitigation plan have been formalized by the audit team, and if he is managed by the CSRO (any issue or action still opened), and if the FT have implemented the mitigation plan (mainly significant and major risks )"	"1. Analyze the Pentest report. Is the black/grey box Pentest report validated ?
2. If YES, validate the Pentest report (and share the mitigation plan)
3. Mitigation plan follow up (Control #28)
4. Validation of the mitigation plan + Update the documents + date of control
5. If NO, Pentest report writting : Results and mitigation plan modified by the Pentest service provider
6. Then, realize the actions #3 and 5"	"Planification of the Pentest realization (Schedule : Pentest for each new major release, or at least once a year). Identification of the Pentest service provider (As already mentioned, this activity could be realized by G3C)
Definition of the Pentest details/context (perimeter, purpose, prerequisites, accounts, IAM, ...)"	"Pentest has been executed by an external entity
A vulnerability mitigation plan has been established"	"Analytics
EE"	"Vulnerability mitigation plan regarding external Pentest
Pentest audit reports (initial and re-audit reports)"	"In accordance with each feature team (and CSRO), as soon as a major release is developed, a new labelization will be made. This audit will be realized once a year too, if there is no significant modification made on the XaaS 
on recommendation (vulnerability to be patched, a component version to upgrade, ...)
->As soon as a new major relaease is edited for production
->If there is no new major relaease, at least once a year"	"Security committee with each CSRO : 
Is the White box Pentest report validated ?
Is the mitigation plan is implemented ?"		"1. Analyze the Pentest report. Is the black/grey box Pentest report validated ?
2. If YES, validate the Pentest report (and share the mitigation plan)
3. Mitigation plan follow up (Control #28)
4. Validation of the mitigation plan + Update the documents + date of control
5. If NO, Pentest report writting : Results and mitigation plan modified by the Pentest service provider
6. Then, realize the actions #3 and 5"	"Audit report that contains :
Vulnerability assessment
Risk assessment
Mitigation plan"			" - First view : Pentest realized for the last major release, or at least once in the last year (Y/N)
 - Second view : Number of vulnerabilities
 - Third view : Number of vulnerabilities closed within the mitigation plan follow-up
 - Fourth view : Number of high and very high level vulnerabilities that are still open"	Yes
	34	X2	Data destruction	"Control plane
Ressource plane
For both, ensure that all sensitive datas (FT or customer datas) are well erased on the XaaS ressources to prevent data retrieval"		Prevent data retireval after erase	"Check if there is some asssets that handle data (ressource plane, control plane - FT datas, customer data)
Check if there is a mechanisms that prevent the data retrieving after the erase
This control must be realized in coherence with the control #36 and 35"	"1. Check if there is any change for the mechanisms to prevent data retrieving
2. If YES, validate the modifications of the data destruction mechanisms
3. Check the modifications and impacts on the data destruction mechanisms
4. Check if the change still allow to prevent data retrieving
5. Collect and update proofs and documents
6. Update the date of control
7. If No, realize the actions #5 and 6 "	"Check if these mechanisms are efficients, and if they are compliant with the SG requirements
Check the chosen mechanisms for the API, the type of storage, the controller, and the load balancing services"	When a  data (FT or customer) is deleted, there is no way on the XaaS to retrieve it		"Compliance with Plateform’s Data disposal requirement
Compliance with Req#36 Data Storage Encryption"	If there is no change, once a year	"Annual security committee with each CSRO : 
is any change for the mechanisms to prevent data retrieving?"		"1. Check if there is any change for the mechanisms to prevent data retrieving
2. If YES, validate the modifications of the data destruction mechanisms
3. Check the modifications and impacts on the data destruction mechanisms
4. Check if the change still allow to prevent data retrieving
5. Collect and update proofs and documents
6. Update the date of control
7. If No, realize the actions #5 and 6 "	Details about the mechanisms to prevent data retrieving 				No
	35	X2	Data storage encryption	"Control plane
Ressource plane
For both, ensure that whenever sensitive data are stored, they're cyphered"		Data encryption at rest must be performed on the XaaS	Check if the data storage encryption is efficient, and compliant with the SG standards	"1. Check if there is any change for the Data storage encryption mechanisms
2. Check with the FT the impacts on the Data storage encryption mechanisms
3. Check with the FT if the Data storage encryption mechanisms are still compliant
4. IF Yes, validate the modifications of the Data storage encryption mechanisms
5. Update the date of control
6. If NO, realize the activity #5"	"Check if a study was realized on the XaaS perimeter (wich component must be encrypted regarding the data stored)
Check le level of data handled (regarding the associated control about data classification
Check the details about API, controller, …
Check the details of the data storage encryption solution (Kind of encryption, perimeter, cyher algorithm, key mgmt"	"The encryption mechanism is defined, documented and validated by the CSRO (including perimeter, data classification level …)
The data stored at rest are unreadables without the associated rigths (given by the CSRO)"		"Configuration extract
Detailled encryption mechanism, algorithm,  key management details, …"	"In accordance with each feature team (and CSRO), as soon as a modification is realized about the at rest data storage.
If no modification, once a year"	"Annual security committee with each CSRO : 
Is any change for the Data storage encryption mechanisms?"		"1. Check if there is any change for the Data storage encryption mechanisms
2. Check with the FT the impacts on the Data storage encryption mechanisms
3. Check with the FT if the Data storage encryption mechanisms are still compliant
4. IF Yes, validate the modifications of the Data storage encryption mechanisms
5. Update the date of control
6. If NO, realize the activity #5"	Details about the Data storage encryption mechanisms				No
	36	X2	Encryption between XaaS components	"Control plane
Ressource plane
For both, ensure that between XaaS components, communications are cyphered"		Communications between XaaS components are cyphered	Check if the encryption mechanisms are still implemented between XaaS Components, in compliance with the initial labelization requirements	"1. Check if there is any change for the encryption between XaaS components
2. If YES, Check if all communications (data flows, any type : Web, DB, logs, …) are listed, if there is any security impact, and if the mechanisms are still compliant with the SG requirements
3. Validate the modifications of the encryption between XaaS components
Check if all communications are cyphered (cypher algorithm, key mgmt, …) with a SG validated solution
4. Collect and update proofs and documents
5. Update the date of control
6. If NO, realize the actions #4 and 5 "		"All communications are cyphered (When sniffing the data transfert, no data must be clearly readable, like password, ID, …)
The cypher mechanism are deployed, documented and validated by CSRO"		Flow matrix with details on encryption protocols used for each communication	"Any change about the encryption between XaaS components

If there is no change,Once a year"	"Annual security committee with each CSRO : 
any change for the encryption between XaaS components?"		"1. Check if there is any change for the encryption between XaaS components
2. If YES, Check if all communications (data flows, any type : Web, DB, logs, …) are listed, if there is any security impact, and if the mechanisms are still compliant with the SG requirements
3. Validate the modifications of the encryption between XaaS components
Check if all communications are cyphered (cypher algorithm, key mgmt, …) with a SG validated solution
4. Collect and update proofs and documents
5. Update the date of control
6. If NO, realize the actions #4 and 5 "	Encryption mechanisms details				No
	37	X2	Admin traceability	"Control plane
Ressource plane
For both, ensure that all admins actions are logued if they are not already managed by the Bastion"		Ensure traceability of all admin operations on the XaaS	Check if there is some changes about the administrators traceability mechanisms, implemented during the initial labelization phase	"1. Check if there is any change about the administrator traceability
2. If YES, validate the bastion usage and the administrator traceability through it
3. Check with FT if the logs about admin activities are still managed by the bastion
4. Collect and update proofs and documents
5. Update the date of control
6. If NO, realize the actions #4 and 5 "	"Ensure that the dedicated procedure is formalized, and the list of activities/events that generate an administrator log is still formalized and up2date
The procedure/list include the details of these events, the involved asset and user account, the type of privileges (IAM matrix and associated logs, ...)  "	All the actions/Events generated by administrators activities on the XaaS assets are produced and availables XaaS		"Matrix of the actions/events that geenrate a log for the administrators activities 
Extract of logs for administrator actions through bastion on a XaaS asset"	"Any change about the administrator traceability

If there is no change,Once a year"	"Annual security committee with each CSRO : 
1. There is change about administrator traceability ?
2. Are the logs about admin activities still managed by the bastion ?
3. Is documentation updated ?"		"1. Check if there is any change about the administrator traceability
2. If YES, validate the bastion usage and the administrator traceability through it
3. Check with FT if the logs about admin activities are still managed by the bastion
4. Collect and update proofs and documents
5. Update the date of control
6. If NO, realize the actions #5 and 6 "	List of the actions/events that generate a log				No
	38	X2	Strong authentication for admins	"Control plane
Ressource plane
For both, ensure that the administrators use MFA to access to assets"		The FT must uses MFA for administration activities on the XaaS	"Check if there is a MFA solution tha used by the FT (directly through the bastion, or another one)
Check if the FT and especialy the privilege accounts use a mandatory MFA solution to realize their activities"	"1. Check if there is any change about the stong authentication for administrators
2. If YES, validate the strong authentication mechanism for the administrators
3. Check the XaaS documentation about the administrators strong authentication mechanisms
4. Collect and update proofs and documents
5. Update the date of control
6. If NO, realize the actions #4 and 5 "	"Check if necessary the details about the curent used bastion, and the curent MFA mechanisms used by FT administrators
Check if there is some derogations about the use of a bastion or the lack of use of a MFA solution on the XaaS perimeter"	FT members use a bastion with Strong Authentication for production environment administration activities.The bastion must enforce the use of MFA mechanism		A quick check realized by the FT and the CSRO (whith an account with privileges) could demonstrate that a MFA cannot be bypassed to be connected on the assets. Screenshots can showing connexion on the XaaS through the bastion. The check can also include a test of direct connection.	"Any change about the administrator strong authentication

If there is no change,Once a year"	"Annual security committee with each CSRO : 
1. Any change about the strong authentication for the administrators  ?
2.  Is the bastion configured to require strong authentication of administrators?
3. Is documentation updated ?"		"Assess if there is changes about MFA use for administrator activities
Validate the strong authentication mechanism for the administrators after the change
Uodate the documentation and the date of control"	Details about the strong authentication mechanisms used				No
	39	X2	Log analysis	"Control plane
Ressource plane
For both, ensure that the logs are managed and analyzed by SOC team"		Supervision and event detection rules must be defined with the SOC team	Contact the SOC to elaborate security scenarios to trigger on log patterns.	"1. Check if some derogations are still currents
2. Check if there is any change about the log analysis strategy / method
3. If Yes, check with FT the security impacts and validate them
4. Check if the changes implementation with the FT and SOC are made and the new rules of supervision are operational
5. Check the new rules of log analysis in production environment
6. Collect and update proofs and documents
7. Update the date of control
8. If NO, realize the actions #6 and 7 "	"Check if necessary the curent details of the log analysis for the XaaS :
Use cases, description, perimeter/XaaS components, action plans (open or closed), status and schedule, …"	"One or several meeting were realized between SOC, CSRO and FT to define what are the use case for the log analysis, the mainattack scenarios and the adapted rules of supervision
SOC and FT (on their own perimeter of responsabilities) has confirmed the implementation of XaaS log analysis and has tested them (CSRO can also check this last item)"		"List of attackscenarios validated
Use case to define the log analysis strategy 
Confirmation from SOC team that alerts are triggered and that a good way of communication is constated between SOC, FT and CSRO"	"Any change about the Logs exploitation by the SOC

If there is no change, once a year "	"Annual security committee with each CSRO : 
1. Any change about the Log analysis?
2. What are the security impact for the changes of log analysis ?
3. Are new rules implemented by SOC and tested for the XaaS?
4. Is documentation updated ?"		"Assess if there is changes about log analysis on the XaaS
Validate the need of change with the FT
Validate the lack of security impact for these changes
Validate with FT and SOC the use case for the new log analysis
Validate with SOC and FT the good iplementation of new log analysis on the XaaS
Uodate the documentation and the date of control"	"Use cases and attack scenarios list
List of security impact for the new log analysis rules and associated mitigations (applied by SOC)
Technical details about the new log analysis rules (form, involved asset, …)
Details about the good implementation of the news rules by OSC team (tests, ...)"	Harmonize the logs to be analyzed by the SOC	"1. Check if some derogations are still currents
2. Check if there is any change about the log analysis strategy / method
3. If Yes, check with FT the security impacts and validate them
4. Check if the changes implementation with the FT and SOC are made and the new rules of supervision are operational
5. Check the new rules of log analysis in production environment
6. Collect and update proofs and documents
7. Update the date of control
If NO, realize the actions #6 and 7 "		No
