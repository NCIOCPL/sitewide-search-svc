## Steps to Run Locally
1. Install docker (if not already installed)
2. Open a command prompt
3. Clone this repository
4. `cd <REPO_ROOT>/integration-tests`
5. `docker compose --project-directory docker-sws-api up --force-recreate`

## Notes
* We use docker for dev testing because ES will no longer run on higher Java versions, so this is the easiest way to get it up and running.
* .NET running locally on a Mac cannot talk to ES because of how NEST always uses the host name to connect to ES and ES exposes the Virtual Machine's hostname/IP that runs Linux on the Mac.
* The `docker up` command above omits the "detached" (`-d`) option to make the containers easier to stop. It may be run either way.
* In order to get the API rebuilt after changes to the code, you must run
  * `cd <REPO_ROOT>/integration-tests`
  * `docker compose --project-directory docker-sws-api down --rmi local`
  * `docker compose --project-directory docker-sws-api build`
  * `docker compose --project-directory docker-sws-api up`
  * Open a second command prompt
  * `cd <REPO_ROOT>/integration-tests`
  * `bin/load-integration-data.sh`
