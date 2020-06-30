# CI, CD & JENKINS

## CI - Continuous Integration

- Developers merge their changes back to the main branch as often as possible.
- The changes are validated by automated testing so that the application is not broken whenever new commits are merged into the master branch.

## CD - Continuous Delivery

- Continuous Delivery is releasing new changes to customers/ clients in a quick and efficient way.  ​
- Having already automated testing using Continuous Integration the changes made can now be deployed and released at any time with just the click of a button.​
- This can be done at any time period but to get the most out of it, it would best be done as early as possible as small scale changes are easier to maintain and troubleshoot.

## CD - Continuous Deployment

- Continuous Deployment goes one step further than Continuous Delivery as it automates the process of deployment.​
- This means that as soon as any change passes all tests it will automatically be released to customers, with no human intervention needed.​
- Only failed tests will not be deployed automatically.

## Jenkins

### Jenkins - Integration Server

- Jenkins is an open source automation tool written in Java with plugins built for Continuous Integration purpose. Jenkins is used to build and test your software projects continuously making it easier for developers to integrate changes to the project and making it easier for users to obtain a fresh build.

### Build steps:

1) Dev updates / changes code
	- Code --> Version Control --> repo
2) Code delivered to build server
	- Jenkins detects chenge, sends to server
3) Builds app
	- Builds new version of app using build-script (.sh file)
4) Testing
	- Using test script
	- Either unit or integrated
5) Return problems
	- Either in UI or as email



### Jenkins Pipeline Set-up

How to add a repo to a pipeline, in a Jenkins Server

1) Enter Jenkins server
2) `New Item`
	- Enter name and type (freestyle project)
3) `Discard old builds`
	- Max 3
4) `GitHub project` - enter WEB url
5) `Restrict where this project can be run` - sparta-ubuntu-node
	***Disabled during set-up***
6) `Source Code Management` - Git
	- CLONE url
7) `Add key`
	- `Kind` - SSH username with private key
	- `id`, `desc` - an internal, unique name
	- `Private key` - enter directly
	- `ADD`
8) Add new key (other) to GitHub, if not there
9) `Branches to build` - /dev/
10) `Additional Behaviours` - Merge before build
								- To master
11) `Build Triggers` - GitHub Hook
12) `Execute shell`
		`cd app
		npm install
		npm test`
13) `Post Build Actions`
	- Git Publisher
		- Push only if succeed
		- Merge results
		- Notes
