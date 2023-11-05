From team "Better than Bobby", Fall SE II 2023: 

Sprint #3 goal, results, and summation:
Goal : Enhance Code Quality, Streamline Deployment, and Integrate a Microservice
User stories, acceptance criteria and business value:
•	User Story: As a developer, I want automated integration testing for our code to ensure that components work together seamlessly.
•	Acceptance Criteria: At least one integration test is written and executed successfully for whatever code is given. I should be able to see the test run and see what happens when the test catches an error or doesn't. This test should log the errors in a report and explain what happened.
•	Business Value: The business value is to catch errors on or before deployment thus enhancing and ensuring a great user experience for our customers because errors will be less likely to be introduced upon release.
•	Result: The team successfully used selenium to go to run through a list of URLs on the locally running development server to catch any broken modules or pages on our website.

•	User Story: As a team member, I want to track defects in our website code, so we can prioritize and fix them.
•	Acceptance Criteria: I should be able to see a defect tracking system or tool in a place that is accessible to everyone on the team. Defects should be documented with descriptions, reproduction steps and the potential impact on our product. The highest defects should be placed in the sprint backlog and lower impact defects should be added to the product backlog.
•	Business Value: The business value here is organization which will allow us to sort and prioritize bugs so they can be fixed in reasonable time frames and by priority. This will help ensure that customers are less likely to encounter game breaking bugs.
•	Result: The team successfully implemented issues into our GitHub repository and started tracking and prioritizing the bugs. The highest impact bugs are reported on our Trello board for immediate resolution.



•	User Story: As a developer, I want to know how long it takes to implement changes from GitHub to production so we can optimize our release process.
•	Acceptance Criteria: I should be able to see a system or tool in place that measures the time from how long it takes to push code to GitHub and then the time it takes to release to production. There should be at least three separate timed releases to get an average measurement. Results should be documented and shared with the team.
•	Business Value: The business value here is to implement metrics so that we can make accurate and timely decisions which will help customers receive timely releases.
•	Result: The team realized through our GitHub pipeline that these deployments/releases were already being tracked. We still manually timed our latest deployment to the server, and it took under 3 minutes to get the new release live.

•	User Story: As a developer, I want the deployment process to be more automated to reduce manual errors and speed up the process.
•	Acceptance Criteria: I should be able to see the current deployment steps are documented. At least one part of the deployment process should be automated using scripts and/or tools. The team should be able to demonstrate automated deployment from GitHub to production without manual intervention.
•	Business Value: This process of automation brings business value because it can reduce errors introduced through manual releases and lessen the time it takes to deploy new code. Customers will see an improvement in timely releases.
•	Result: The team successfully used GitHub actions to implement automation on pushes/merges to different GitHub branches. Upon a merge to a dev branch a Docker container image is automatically rebuilt and pushed to the Docker Hub repository. Upon a merge to the main branch a Docker container image is automatically rebuilt, pushed to the Docker Hub repository and from there the team simply must run a script to automate the pulling and rebuilding on the server. Deployment steps have been demonstrated and documented in a google docs file.

•	User Story: As a student user, I want the website to offer additional features without affecting the main site's performance, this will ensure a seamless game experience.
•	Acceptance Criteria: At least one microservice should be integrated into the website. The microservice needs to run independently and not affect the performance of the main website. The team should be able to demonstrate the added microservice.
•	Business Value: The business value here is that with a microservice the team can implement changes that will not affect system performance overall. Customers will be able to see changes happening without anything detrimental happening to the main systems.
•	Result: The team successfully created a microservice using docker containers. A docker container hosts the main app and another is built which hosts the game descriptions, author, and instructions. The main app container calls the microservice through a sort of API and pulls in the information for the game. If the microservice fails, it does not affect the main system except that information will not be displayed for the games. The main app in no way can edit or affect the microservice.

•	User Story: As a developer, I want to implement semantic versioning and associate release numbers to our deployments, so I can easily track and reference changes in our software across different stages of development.
•	Acceptance Criteria: Every deployment to production is associated with a unique version number based on the semantic versioning system. The version number is composed of three segments: MAJOR.MINOR.PATCH. MAJOR version for incompatible changes, MINOR version for backward-compatible functionalities, PATCH version for backward-compatible bug fixes. Release notes are generated for each deployment, detailing the changes made, associated with the corresponding version number. Developers can easily retrieve and reference a specific version of the deployed software using the version number. The version number is visible to end-users, ensuring transparency about the software's current state.
•	Business Value: The business value here is that customers will be able to keep up with the latest updates in a transparent way. It also adds value to our team so developers can easily switch between different versions of the website or even rollback if necessary.
•	Result: The team successfully implemented GitHub release notes along with semantic versioning. The version number is also displayed on our website that links to the GitHub patch notes. These GitHub patch notes are automatically generated based on pull requests/merges and labelled according to our feature branching.
