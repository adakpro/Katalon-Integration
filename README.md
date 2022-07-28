# ADAKLABS  Katalon Integration
This is an attempt to integrate adaklabs.io into Katalon Studio.

## Getting Started
Follow these instructions to get this sample code run on your local machine.
### Prerequisites
* Has set up a adaklabs.io server on your own machine.
* Has downloaded and installed the latest version of Katalon Studio.
* Has installed Gradle 5.0.

### Installing
Copy the *com* folder into your Katalon project's *Keywords* folder.
Copy the "build.gradle" file into the base folder of your project. Then run the command :
```
gradle katalonCopyDependencies
```

### Updating the Katalon profile
Set following values of the ReportPortal profile to new ones using info from your own profile on adaklabs server.
```
RP_HOST : your adaklabs API host. Ex : http://127.0.0.1:8080/api/v1
RP_TOKEN : 'Bearer' + UUID value. Ex : Bearer f974e133-5f90-4912-9332-5b77d7bbd3d8
RP_NAME : your project's name on adaklabs.
```

### Registering the adaklabs listener
Add the following code snippet into your suites. This will create a launch object named *Sample_Suite* each time the injected suite being executed.
```groovy
@SetUp(skipped = false) // Please change skipped to be false to activate this method.
def setUp() {
	// Put your code here.
	ExecutionEventManager.getInstance().addListenerEventHandle(new ReportPortalListener("Sample_Launch", "Sample_Suite"))
}
```
## Authors
**ehsan khashaee** - *Core service implementation* - [adak](https://github.com/adakpro)
