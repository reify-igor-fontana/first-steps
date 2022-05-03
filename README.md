_This checklist walks a new developer through our projects and build processes._
# First Steps Checklist
* [x] Create a new Reify-specific GitHub account. By the time you reach this list, you should have received an invite to the Reify Health github project. Contact your manager if you've not received that invite.
* [ ] Ensure you have a private reify directory in your home directory: `mkdir -p ~/.reify`
* [ ] Install Java JDK 11 or newer: `brew install openjdk@11`
* [ ] Set up SSH per the instructions in [`lein-git-down`](https://github.com/reifyhealth/lein-git-down/#private-repositories-ssh-authentication):
  * [ ] Generate SSH key and add it to the ssh-agent as per [this doc](https://help.github.com/articles/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent/) (*Important Note*: add `-m PEM` as an argument to the command `ssh-keygen -t rsa -b 4096 -C "your_email@example.com"` as in `ssh-keygen -t rsa -b 4096 -m PEM -C "your_email@example.com"`)
  * [ ] [Create a new SSH key to your GitHub account](https://help.github.com/articles/adding-a-new-ssh-key-to-your-github-account/). Please make sure your SSH key is stored safely. This key should be strictly used for business purposes. Do not use this key on any of your personal accounts.

## Development Data Setup
Each app will have its own dependencies (direnv, nodejs etc). Both apps will be using github packages and homegrown tools so make sure that you start with the Bengal setup so that you'll be able to automatically pull in those dependencies with the required config variables.

# First End to End Run
You need Bengal and Salk up and running in order to have StudyTeam fully functional. 
Follow the below docs in order to get those up and running. 
### Bengal Specific Instructions
To set up your development environment for the first time, follow [these instructions](https://github.com/reifyhealth/bengal#set-up-development-environment). You should be able to do the following three things:
  * [ ] [Set up development and test database](#development-data-setup)
  * [ ] [Run tests](https://github.com/reifyhealth/bengal#testing)
  * [ ] [Run the REPL](https://github.com/reifyhealth/bengal#repl-startup)

### Salk Specific Instructions
Once you've confirmed that you can run `bengal` in the command line and you have local databases set up, follow the setup instructions for the version of Salk you wish to run, either _Site_ or _Sponsor_.

[Salk Site](https://github.com/reifyhealth/salk#local-development-quick-start). 
[Salk Sponsor](https://github.com/reifyhealth/salk-sponsor#local-development-quick-start). 

You should be able to do the following things in Sponsor and/or Site:
#### Site

* [ ] Set up [`salk`](https://github.com/reifyhealth/salk)
  * [ ] Set up [styling](https://github.com/reifyhealth/salk#compiling-the-css-stylesheet) and build CSS/SASS assets
  * [ ] Run [tests](https://github.com/reifyhealth/salk#testing) for all targets
  * [ ] [Run the apps](https://github.com/reifyhealth/salk#compiling-and-running-applications) in demo mode
  * [ ] Run `salk` app as dev build in [remote mode](https://github.com/reifyhealth/salk#remote-vs-demo-mode). Visit it in your browser.
  * [ ] Read through all the architecture docs in the README.
#### Sponsor 

* [ ] Set up [`salk-sponsor`](https://github.com/reifyhealth/salk-sponsor)
  * [ ] Set up [styling](https://github.com/reifyhealth/salk-sponsor#compiling-the-css-stylesheet) and build CSS/SASS assets
  * [ ] Run [tests](https://github.com/reifyhealth/salk-sponsor#testing) for all targets
  * [ ] [Run the apps](https://github.com/reifyhealth/salk-sponsor#compiling-and-running-applications) in demo mode
  * [ ] Run `salk-sponsor` app as dev build in [remote mode](https://github.com/reifyhealth/salk-sponsor#remote-vs-demo-mode). Visit it in your browser.
  * [ ] Read through all the architecture docs in the README.

## StudyTeam Documents

### Backend services - eDOA and eSource

The setup of both projects [`eDOA`](https://github.com/reifyhealth/edoa-service) and [`eSource`](https://github.com/reifyhealth/esource-service) requires the installation of these tools, as described in the Readme of [eSource](https://github.com/reifyhealth/esource-service#requirements) project. As those projects work the same, you can apply the same bellow for both:
  * [ ] [Quickstart and REPL](https://github.com/reifyhealth/esource-service#quickstart)
  * [ ] [Run Tests](https://github.com/reifyhealth/esource-service#test)

### Frontend services - Study Sheet and eDOA React Components

Once getting the Backend services running, you can start the [`Study Sheet`](https://github.com/reifyhealth/study-sheet) service, that its the frontend of StudyTeam Documents product.
  * [ ] [Requirements](https://github.com/reifyhealth/study-sheet#requirements)
  * [ ] [Quickstart](https://github.com/reifyhealth/study-sheet#requirements)
  * [ ] [Commands](https://github.com/reifyhealth/study-sheet#requirements)

# Miscellaneous
* [ ] Set up [pantry](https://github.com/reifyhealth/pantry) which is a shared package of spec definitions and other utility function used in Bengal and Salk. This will already be pulled into Salk and Bengal but you can peruse it locally if you ever end up contributing to it.
  * [ ] Run tests
* [ ] Check out [serde](https://github.com/reifyhealth/serde) for another shared resource of de-serialization utilities that are shared across applications.
* [ ] If you haven't had a product walkthrough, try some of the features using the [QA scripts](https://github.com/reifyhealth/qa-docs/blob/master/QA.md#areas-to-qa) as a guide. Please reach out to the QA team if you have questions on what is most useful or interesting to QA.
* [ ] Set up and try [hooke](https://github.com/reifyhealth/hooke), the admin application
  * [ ] Install [yarn](https://yarnpkg.com/) and build `hooke`
  * [ ] Add `{"role": "reifyadmin"}` under `app_metadata` to the admin Auth0 user (`<name>+admin-local@reifyhealth.com`) on the [Users page](https://manage.auth0.com/#/users)
  * [ ] Run `hooke` server
  * [ ] Run `bengal` server and verify `hooke` can interact with `bengal`
  * [ ] Try a couple of workflows mentioned in [this guide](https://reifyhealth.atlassian.net/wiki/spaces/QA/pages/253132897/StudyTeam+Configuration+Guide)

## Testing and Staging Access

Refer to [bengal's readme](https://github.com/reifyhealth/bengal#authentication) for how to get access to StudyTeam as well as how to get administrator access used by ReifyAdmin and a few other internal apps.

Request access and administrator privileges for your SSO user (&lt;alias&gt;@reifyhealth.com) in testing and staging environments.

* [ ] Confirm you can log in to site and sponsor StudyTeam apps in [testing](https://testing.studyteamapp.com).
* [ ] Confirm you can log in to site and sponsor StudyTeam apps in [staging](https://staging.studyteamapp.com).
* [ ] Confirm you can log in to ReifyAdmin in [testing](https://reifyadmin-testing.studyteamapp.com).
* [ ] Confirm you can log in to ReifyAdmin in [staging](https://reifyadmin-staging.studyteamapp.com).
