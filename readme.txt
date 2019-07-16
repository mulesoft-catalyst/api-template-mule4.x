TEMPLATE NOTES
==============

The following template needs to be used as follows:

1. Rename:
	- Mule Project from "api-template" to "<YOUR_API_NAME>-impl"
	NOTE: Notice the "-impl" suffix. This will help the CI/CD tooling to differentiate between an API spec (RAML) vs.
	      the actual Mule implementation.
	- pom.xml:
		- <artifactId>api-template</artifactId> with your "<YOUR_API_NAME>-impl" (e.g. system-my-cool-api-impl)
		  NOTE: Notice the "-impl" suffix. This will help the CI/CD tooling to differentiate between an API spec (RAML) vs.
	      		the actual Mule implementation.
		- <name>API Template</name> with the "<YOUR_DISPLAY_API_NAME>" (e.g. My Cool System API)
		- Configure the SCM tags as needed 

2. Export RAML spec from Design Center 

3. Extract the contents of the exported RAML spec into src/main/resources folder

4. Rename the <YOUR_API>.raml to api.raml (you will need to remove the current one first)

5. Right click RAML spec > Mule > Generate Flows from REST API
   Note: If nothing gets created then most likely there is an issue with your RAML spec

6. Remove "api-main" and "api-console" flows

7. In the config-<environment>.properties update the value of api.id from API Manager or manage them outside of the template in case of an on prem deployment

9. The resulting api.xml (auto-generated) should be treated as the interface of the API (e.g. TEMPLATE-EXAMPLE-API.xml) 

10. The implementation should happen on a separate configuration file (e.g. TEMPLATE-EXAMPLE-API-IMPL.xml) and referenced by the interface through flow-ref's

11. Note that the provided TEMPLATE-EXAMPLE-API-IMPL.xml shows an example on the minimum logging any Mule implementation flow should have

12. There is also a sample munit test that validates the mimumum logging described in the line above

13. If testing locally (Anypoint Studio) you need to pass the mule.key as a JVM argument (e.g. -Dmule.key=somekey)

14. In order to run the munit tests from command line, you need to pass the following JVM arguments: -Dmule.env=munit -Dmule.key=munit

15. Lastly, TEMPLATE.raml, TEMPLATE-EXAMPLE-API.xml and TEMPLATE-EXAMPLE-API-IMPL.xml and TEMPLATE-EXAMPLE-API-IMPL-test-suite.xml files should be deleted


SETUP SECURE PROPERTIES
=======================

Install from Exchange and use


MAVEN SETUP
===========

1. Please note that the following configuration should be in the settings.xml within your <USER_HOME>/.m2 folder:
	<!-- HA development wide access to Mule Nexus EE repositories -->
	<server>
	    <id>MuleRepository</id>
	    <username><NEXUS_USER></username>
	    <password><NEXUS_PASSWORD></password>
	</server>
	<!-- HA Anypoint Exchange access -->
	<server>
		<id>Exchange2</id>
		<username><ANYPOINT_USER></username>
		<password><ANYPOINT_PASSWORD></password>
	</server>
	
2. Maven 3.5+ is required

3. Oracle JDK 1.8.x 64 bits is required (1.9 is not supported yet)