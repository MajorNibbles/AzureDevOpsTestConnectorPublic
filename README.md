# Azure DevOps Test Connector
A [Visual Studio 2019 extension](https://marketplace.visualstudio.com/items?itemName=MadeUpExtensions.AzureDevopsTestConnector)  allowing users to link Test Classes and SpecFlow Feature files with Azure DevOps Test Plans/Suites and Cases using tracking attributes or comments.
It syncs test case titles with your Test Solution Test Method names, as well as also syncing your SpecFlow Scenario Steps.
The ADO Test Connector now also automatically [Associates automated tests between VS and ADO](https://docs.microsoft.com/en-us/azure/devops/test/associate-automated-test-with-test-case?view=azure-devops). Massively speeding up the existing VS functionality 

## Why Use it?
This allows a Test Automation Engineer to quickly synchronise their latest work in Visual Studio with Azure DevOps, saving time by automatically creating and linking Test Plans, Test Suites (both static and requirements based) Test Cases and Specflow Test Steps

## How to use it
 1. First install the extension from the Visual Studio market place.
 2. Once installed go to Options > Tools > Azure DevOps Test Connector
    and fill out the following settings:
	 
	 2. **Azure DevOps instance URL**: The base URL of the Azure DevOps instance you want to connect to, this can be both the legacy and new URL structure.
	 
	 2. **Comments instead of Attributes**: If true then all test references (Plan/Suite/Case) in the Test Class will be added as comments *(e.g. //TestCaseId(123456))*. If false than the references will be added as Attributes *(e.g. [TestCaseId(123456)])*.
	 
	 2. **PAT Code**: Your Personal Access Token, found in [Azure DevOps](https://docs.microsoft.com/en-us/azure/devops/integrate/get-started/authentication/pats?view=azure-devops#create-personal-access-tokens-to-authenticate-access).
	 
	 2. **Test Plan/Suite/Case Attribute Name**: *What ever you set here will be used to create the Test Plan/Suite/Case Attributes or Comments. *(e.g. "TestCaseId(~)" will result in "//TestCaseId(123456)".. NOTE: ~ is replaced with the Test Case ID. Changing this pattern once the comment/attribute has already been created will result in parsing ignoring the existing test case!)*.
 3. Navigate to your class file with Test Methods in it.
 4. Right click anywhere in the Test Class or Feature File.
 5. Select "Sync Azure DevOps Test Cases"
 6. If no Test Plan attribute can be found a prompt will appear for you to either enter an existing Test Plan's ID OR enter a new Test Plan's name.
 7.  If no Test Suite attribute can be found a prompt will appear for you to either enter an existing Test Suite's ID OR enter a new Test Suite's name. If a new Test Suite's name is entered a second prompt will appear asking if you want it to be [Requirements](https://docs.microsoft.com/en-us/azure/devops/test/create-a-test-plan?view=azure-devops#add-a-requirement-based-test-suite-and-select-backlog-items-to-test) based, to link the new Test Suite with a requirement simply enter a Requirement WorkItem's *(e.g. Backlog Item)* ID to link it to. If this is left BLANK it will create a Static Test Suite.
 8. A prompt will now appear asking if you would like to Automatically Associate the test case in Azure DevOps with the test solution. The entry should be the dll in which the test class is held. Leave this blank to not Associate the Test Case.
 8. The extension will now scan the Test Class and create/update any Test Methods in Azure DevOps, linking them to the Test Suite.
 9. Test Case names will be formatted automatically. Any capitals or underscores will be changed into spaces, E.g.
 GivenIHaveDoneThis_ThenThisWillHappen = Given I Have Done This Then This Will Happen
 10. If syncing a specflow feature file the extension will also upload any test steps to the test case in Azure DevOps.
 11. Once the Creation/Updating of the Test Methods has been completed it will then add Test Plan/Suite/Case attributes or comments to the Test Class (depending on the option set in section 2b.

## Notes
 - Test Plan and Test Suite attributes/comments are added just above the class declaration
 - Test Case attributes/comments are added just above the Test Method signature
 - Currently supports MSTest, NUnit and SpecFlow Feature files
