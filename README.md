# Azure DevOps Test Connector
A Visual Studio 2019 extension  allowing users to link Test Classes with Azure DevOps Test Plans/Suites and Cases using tracking attributes or comments.

## Why Use it?
This allows a Test Automation Engineer to quickly synchronise their latest work in Visual Studio with Azure DevOps, saving time by automatically creating and linking Test Plans, Test Suites (both static and requirements based) and Test Cases

## How to use it
 1. First install the extension from the Visual Studio market place.
 2. Once installed go to Options > Tools > Azure DevOps Test Connector
    and fill out the following settings:
	 
	 2. **Azure DevOps instance URL**: *The base URL of the Azure DevOps instance you want to connect to, this can be both the legacy and new URL structure*.
	 
	 2. **Comments instead of Attributes**: *If true then all test references (Plan/Suite/Case) in the Test Class will be added as comments *(e.g. //TestCaseId(123456))*. If false than the references will be added as Attributes *(e.g. [TestCaseId(123456)])*.
	 
	 2. **PAT Code**: *Your Personal Access Token, found in [Azure DevOps](https://docs.microsoft.com/en-us/azure/devops/integrate/get-started/authentication/pats?view=azure-devops#create-personal-access-tokens-to-authenticate-access).
	 
	 2. **Test Plan/Suite/Case Attribute Name**: *What ever you set here will be used to create the Test Plan/Suite/Case Attributes or Comments. *(e.g. "TestCaseId" will result in "//TestCaseId(123456)")*.
 3. Navigate to your class file with Test Methods in it.
 4. Right click anywhere in the code.
 5. Select "Sync Azure DevOps Test Cases"
 6. If no Test Plan attribute can be found a prompt will appear for you to either enter an existing Test Plan's ID OR enter a new Test Plan's name.
 7.  If no Test Suite attribute can be found a prompt will appear for you to either enter an existing Test Suite's ID OR enter a new Test Suite's name. If a new Test Suite's name is entered a second prompt will appear asking if you want it to be [Requirements](https://docs.microsoft.com/en-us/azure/devops/test/create-a-test-plan?view=azure-devops#add-a-requirement-based-test-suite-and-select-backlog-items-to-test) based, to link the new Test Suite with a requirement simply enter a Requirement WorkItem's *(e.g. Backlog Item)* ID to link it to. If this is left BLANK it will create a Static Test Suite.
 8. The extension will now scan the Test Class and create/update any Test Methods in Azure DevOps, linking them to the Test Suite.
 9. Once the Creation/Updating of the Test Methods has been completed it will then add Test Plan/Suite/Case attributes or comments to the Test Class (depending on the option set in section 2b.

## Notes
 - Test Plan and Test Suite attributes/comments are added just above the class declaration
 - Test Case attributes/comments are added just above the Test Method signature
 - Currently only support MSTest and NUnit tests
