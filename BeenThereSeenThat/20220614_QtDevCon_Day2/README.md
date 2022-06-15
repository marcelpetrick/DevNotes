# 20220615 Qt Dev Con - day 2

## how i learnt to stop. eorrying and lobe Unicode - guiseppe d'angelo
* most important part about cpp is tooling, so use all the available tooling (clazy, clang-tidy,..) to make your code as safe as possible

--------

## cross platform CI/CD setup - make it easy - Lukas Kosinski
* retired developer, does not code so much anymore
* he doesn't claim the title of genius: evangelist of ci/cd-pipelines in Qt projects
* happy father of six guinea pigs

### agenda
* CI/CD basics
* example gitlab ci/cd setup for qt project
* introducing ci/cd in legac projects

* a story: former company, he worked as developer, no tests,  no conventions, no ci/cd, much testing by testers, but not ci/cd: but the company did not listen
  * when a new release for mac was prepared, so he struggled to do this; also create a release on friday; .. you know what follows
* but a release should be done on organisational level; on servers, runners, .. not on dev-computers; everyone needs access
* safety, save time and money

### what makes up CI/CD?
* cotinuous integration: code should not be broken when it is integrated
  * unit-tests, static checking, create current documentation
* continuous delivery:
  * create installers, upload stuff, sign installers, ..
* one rule: Keep the software in releaseable state (CI/CD golden rule): take the code and release it at any moment

### Hygiene in work with CI/CD
* despite having the pipeline, always run tests locally before pushing
* even the best setup won't catch everything
* aways optimize pipeline time
### ci/cd tools to choose
* code hosting service
* ci/cd solution
* ci/cd tasks runner
* artifacts repository

### what to choose as CI/CD tasks runner?
* also matter of security (office or shared one?)
* mac mini: android, ios, macos, linux with docker, windows: five types on one machine

### example gitlab ci/cd pipeline
* pipeline; stage; jobs
* qt 6.3, cmake as the build system, ruby scripts
* the example project works on every platform: because it is just a single window xD
* before you need runners: one for ios and mac-jobs, one for window, android and linux
* gitlab-ci.yaml file (goes to root folder of gitlab)
  * defines the stages: build, test, packing
  * put the build-instructions into one script to run it as well locally
  * also move the result to the next folder for test
  * if it succeeds, then a green checkmark, else a red cross
* every job has a job log; 

### gitlab ci/cd variables
* TEAM_ID $ENV{TEAM_ID}
* how to keep sensitive data secret?
* protected variables, make yourself maintainr, only maintainer can push to protected branches and merge on them; so no one can extradit protected variables

* include templates from other repositories:  company wide branded template (which has some benefits)

### why ci/cd in legacy projects is challenging?
* low code quality, huge number of little issues;
* what to utomate first? wat to automatize first? compiling, packaging, then regression tests

ci/cd makes sw engineers more productive and happier; impact on business: either have a high-quality sotware code base which allows easy releases or have low quality code where it is hard to release
* gitlab.com; kosadev; example ci gitlab .. (add from photo)

* relesae for ios is done with fastlane: release app to appstore and google play immedietaly
* google file based istribution for testing
* todo check what means CTA?