ManageConfig.cs → configuration management
ManageProxy.cs → proxy-related operations
ManageSyncService.cs → service synchronization
UsersAndRoles.cs → users/roles/permissions
VerificatoreNome.cs → service-name validation
WSDLParser.cs → WSDL processing
XmlInputOutput.cs / XmlInputOutputXslt.cs → XML/XSLT processing
XmlWriter.cs → XML generation

jfweb-dashboard.wsclient

Dow

The

모모

src

main

java

it.bnl.servicerepository

27

serviceheader

28

input

29

AhDestination

30

AhMessageInformation 31

AhOrigen

32

AhSecurity

33

BackendHeaderInput

34

HeaderAppl

35

ObjectFactory

36

package-info.java

37

output

38

AhApplStatusR

39

BackendHeader Output

40

41

HeaderAppl

42

ObjectFactory

43

package-info.java

44

servicemanager

45

> input

46

output

47

> zj40001

48

test

49

> Java

50

M4 README.md

51

wsdl

52

XSD backend-header-input.xsd

55

56

X50 backend-header-output.xsd

57

XSD sm-error.xsd

58

X50 sm-header.xsd

59

DI. ZJ40001.wsdl

60

XSD ZJ40001IDATA.xsd

61

XSD ZJ400010DATA.xsd

62

१७

m pom.xml



zj40001

input

DataAppl

ObjectFactory

package-info.java

output

DataAppl

ObjectFactory

package-info.java

soapservice

ObjectFactory

package-info.java

ZJ40001Request

ZJ40001Response

wsdl

ZJ40001WSDL

ZJ40001WSDL_Service

.gitattributes



Jfweb-dashboard.webapp

src

> jfweb.root

main

java

it.bnl.jfweb

> action

>

bean

> config

> context

controller

JfwebRequestProcessor

> exception

> listener

> logging

> plugin

> request

> servlet

> taglib

> util

General Constants

> webapp

> test

M pom.xml




bnissocore

bnisso-core

main

java

it.bnl

jfweb.loginsso

BNLJFWebLogFormatter

logi

ErrorEncode

HeaderField

JFWebLoginLogger



JFWebLogin Module



JFWebPrincipal


Versioninfo



logging

BNLLogFormatter


BNLLogger

BNLLogUtil

$50

resources

>test

M pom.xml

>bnisso-core.build


>bnisso-core-dist


@gitignore



.gitlab-ci.yml


M4 README.md



Hi Daniele,

During the investigation, we identified the following findings:

1. URL mismatch: The URL provided in the request is "https://qa-sminternetcorp-biz-secure.echonet", whereas the corresponding staging host alias is "ga-sminternetcorp-biz-secure.staging.echonet". The staging hostname in the request appears to be incorrect, as the "staging" keyword is missing and the hostname differs.

2. No matching logs found: We searched the available logs for the requested date and time range. However, no matching logs were found for the specified URL. We also checked the logs available for the past month (attached for reference), but the URL provided in the request was not found.

Could you please verify the correct URL/environment and confirm whether we should proceed with the staging URL?

Regards,
Mannoj

bnpp.env: "qual" and Tipo: "INTRANET" and log.file.path:*/apps/web/SM_Intranet/Service ManagerFE/logs/0*_proxy.log and RSMHostAlias: "smrisparmiofinalizzato.bnl.echonet" and targetUrl: *


Hi Daniele,

I investigated the existing INTERNET configurations and the possibility of exposing the Flow Estrazione PIN service through SM INTRANET.

INTERNET configuration

Both Qualification ("smflowestrazionepincoll.bnl.echonet") and Production ("smflowestrazionepin.bnl.echonet") aliases are configured with the RD connection, using HTTP to "tibco.isle02:3083".

INTRANET investigation

- The requested aliases are not present in the Qualification or Production INTRANET configuration repositories.
- In Production INTRANET, I found two existing aliases ("smmobiletoken.bnl.echonet" and "smgptoolmobiletoken.bnl.echonet") configured to route to "10.238.60.64:3083".
- Kibana logs show requests from these aliases to the Flow Estrazione PIN endpoints on the same IP and port. The matching records show HTTP 408 responses, so successful processing is not confirmed.
- No matching traffic to this IP was found in the Qualification INTRANET logs for the selected one-year period.

I have attached the relevant Production INTRANET configuration and Kibana findings for reference.

Could you please confirm whether "10.238.60.64" is the intended INTRANET backend IP for Flow Estrazione PIN, or provide the correct IP if different?

Based on the existing Production INTRANET configuration and logs, the two aliases mentioned above could be considered as references when evaluating the reuse of an existing RSMHostAlias.

Thanks.
