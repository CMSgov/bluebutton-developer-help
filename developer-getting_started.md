# Developer - Getting Started with BBAPI

Questions often asked by developers when looking at integrating a new API   include:
1. [Where can I find the API documentation?](#where-can-i-find-the-api-documentation)
2. [What protocols are used by the Blue Button API?](#what-protocols-are-used-by-the-blue-button-api)
3. [What format is the data published in?](#what-format-is-the-data-published-in)
4. [Do I need to register my application?](#do-i-need-to-register-my-application)
5. [How do I register as a Developer?](#how-do-i-register-as-a-developer)
6. [What is a typical scenario for using the API?](#what-is-a-typical-scenario-for-using-the-api)
7. [What are the requirements for my environment?](#what-are-the-requirements-for-my-environment)
8. [What are the data implications for ACOs when using BBAPI?](#what-are-the-data-implications-for-acos-when-using-bbapi)
9. [What are the data implications for any organization with a registered BBAPI application?](#what-are-the-data-implications-for-any-organization-with-a-registered-bbapi-application)
10. [Are there any restrictions on development environments I can use?](#are-there-any-restrictions-on-development-environments-i-can-use)
11. [Is there a test system I can use?](#is-there-a-test-system-i-can-use)
12. [How often is BBAPI information updated?](#how-often-is-bbapi-information-updated)

## Where can I find the API documentation?
If you are reading this online then you have already found the Blue Button API (BBAPI) developer documentation. Otherwise point your browser at:
[Blue Button API Application Developer Documentation](https://hhsidealab.github.io/bluebutton-developer-help/)
https://hhsidealab.github.io/bluebutton-developer-help/

## What protocols are used by the Blue Button API?
BBAPI is built using some key specifications and protocols. These include:
	- [OAuth2.0](https://oauth.net/getting-started/) for Access Authorization.
	- [HL7 Fast Healthcare Interoperability Resource](https://www.hl7.org/fhir/) (FHIR) specification.
	- [Pre OAuth Entity Trust](https://github.com/hhsidealab/POET) (POET) Application Endorsement Protocol
	 
## What format is the data published in?
BBAPI provides data in two formats:
	- [JSON](http://www.json.org)
	- [XML](http://www.xmlfiles.com/xml/xml_intro.asp)

## Do I need to register my application?
As a Developer you must create an account on the BBAPI platform in order to register your application(s).

## How do I register as a Developer?
There are two phases in the launch of the BBAPI platform:
	1. Pilot
	2. General Availability
To learn more about the timeline for general availability of the bBAPI platform go to: http://go.cms.gov/bluebutton. 
### Pilot
During the pilot phase Developers will receive an invitation from the BBAPI team to join the pilot program. The invitation will take the form of an email with an embedded link. Clicking on the link will open a registration page that enables a Developer account to be created.
### General Availability
In this phase Developers will be able to directly access a Developer Registration phase on the BBAPI portal.   

## What is a typical scenario for using the API?
BBAPI enables a Medicare beneficiary to authorize a registered application to retrieve their claims information.  Up to three years of information covering Medicare Part A, B and D claims can be retrieved. The data is formatted in the FHIR Release 3 (stu3) ExplanationOfBenefit Resource format.
Since a registered application requires the specific authorization of an individual beneficiary potential use case scenarios include, but are not limited to:
	- On-boarding and Check-in applications
	- Personal Health Record applications
### On-boarding and Check-in applications
When a beneficiary joins a program or is new to a healthcare organization a registered on-boarding or check-in application could be configured to ask the beneficiary if they wish to share their full Medicare claims history with their new provider. 
The application would guide the beneficiary through: 
	- Authenticating with the BBAPI platform
	- Authorizing the application to receive their claims information
Once authorization has been given the application can check for new claims information on a weekly basis, or whenever a beneficiary visits the facility. 
The application could also retrieve claims information between beneficiary facility visits in order to check for new claim events from other facilities that generate Medicare claims.
### Personal Health Record applications
If an organization provides their own, or a third-party, Personal Health Record (PHR) system the application could be registered with BBAPI enabling a beneficiary to import their Medicare information into their PHR.
After the beneficiary authorizes the application it could be configured to check for new claims information whenever the beneficiary opens the application. 

## What are the requirements for my environment?
In order to take advantage of BBAPI and access a beneficiary's Medicare claims information an organization will need to support the following environment:
	- An Internet-facing server to act as an endpoint to handle OAuth2.0 callbacks from the BBAPI Authorization process.
	- Data can be retrieved in JSON or XML format. Claims information will be presented in the FHIR STU3 ExplanationOfBenefit format. 
	- BBAPI is a RESTful API. Therefore, the registered application must be able to:
		- Handle an OAuth2.0 authorization process
		- Make RESTful requests to BBAPI for beneficiary information
		- Process and store the received JSON or XML data.
	- BBAPI provides unto 3 years of Medicare claims information for a beneficiary. The FHIR API enables date parameters to be provided in a data request in order to request only the latest information. 

## What are the data implications for ACOs when using BBAPI?
	- Many Accountable Care Organizations (ACOs) receive a monthly bulk data feed from CMS that contains claims information for the beneficiaries in their care.  The BBAPI data is refreshed on a weekly and monthly basis. As such claims may appear through BBAPI before they are included in the monthly claims feed. ACOs will need to manage the de-duplication of data received via the    two data channels.
	- If a beneficiary has opted out of sharing information via the monthly bulk data feed they can still choose to share their information via BBAPI. The two authorizations are totally independent of each other.

## What are the data implications for any organization with a registered BBAPI application?
	* BBAPI is a consumer-directed exchange. Each individual Beneficiary gives explicit authorization to each application. 
	* An application that is registered with BBAPI has no access to beneficiary information until a beneficiary gives an explicit authorization.
	* The BBAPI platform provides a dashboard for beneficiaries. This enables a beneficiary to revoke access to a registered application at any time.
	* The BBAPI administration and security team can choose to revoke the key for a registered application, or throttle the number of API calls allowed by an application if suspicious API usage is detected. Revocation or Throttling of an application impacts the ability of a registered application to access the information for any beneficiary that has authorized access to their data. 

## Are there any restrictions on development environments I can use?
You are free to use any development languages for your application. 
The BBAPI team is working to provide code samples and interaction examples in the following formats:
	- Curl
	- Postman
	- JAVA
	- Javascript
	- .Net
	- Python
	- PHP
This is an ongoing process. You are welcome to provide examples for us to incorporate. 

## Is there a test system I can use?
BBAPI provides a test system. It has a small subset of synthetic information. 
The test system can be accessed here:
http://test.bluebutton.cms.gov

## How often is BBAPI information updated?
	- Weekly:
	Part A and Part B
	- Monthly:
	Part D
	
