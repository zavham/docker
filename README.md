# 13-beta-product-release-gold 

Links to documents:
=================


* Waffle - https://waffle.io/chas-academy/13-beta-product-release-gold

* Figma Digital Prototype - https://www.figma.com/file/XpRhpmJiZ0zx5pEn9L9xK9TX/%C3%A4rendehantering

* Database Structure - https://docs.google.com/document/d/1j3sNRhc00jjowH8NPBP0s1_yv66euTqujkUJe0vgyws/edit

* Personas - https://docs.google.com/document/d/1hYNcN7iv0qej72wIAcYNTBWNU8TsIygWDPHKbU_bX0U/edit

* Budget - https://docs.google.com/spreadsheets/d/1eZdx7tB3UNcasHimysfUmG62TDGHG7PUjn3cLffe-r8/edit

* website specification  - https://docs.google.com/document/d/1g2GDwGQ_MI2DAaV-Ttk_jz_eDCes5MbEbEYrgpV2vVI/edit



# Project Boilerplate
This is the project boilerplate which will get you started. For any questions regarding the stack, please use our [#help](https://chasacademy.slack.com/messages/C61J8A678/#help) channel in Slack.

Table of contents
=================

<!--ts-->
   * [Directory Layout](#directory-layout)
   * [Quickstart](#quickstart)
   * [Installation](#installation)
   * [Usage](#usage)
      * [Bash Commands](#bash-commands)
<!--te-->

## Directory Layout
```bash
./
├── /api                    # Directory for backend, see below for more detail (created when running /bin/install)
├── /client                 # Directory for frontend, see below for more detail (created when running /bin/install)
├── docker-compose.yml      # Defines Docker services, networks and volumes, do not touch unless you know what you are doing
└── README.md               # The file you are reading right now
```

**NOTE**: The `api` and `client` folders are in fact separate repositories (git submodules):

- Backend: [https://github.com/chas-academy/project-api-boilerplate](https://github.com/chas-academy/project-api-boilerplate)
- Frontend: [https://github.com/chas-academy/project-app-boilerplate](https://github.com/chas-academy/project-app-boilerplate)

This means when making changes to either you need to commit and push in the separate repositories.

## Quickstart
## Install and Start the Apps
1. First download and install the [Docker Community Edition](https://www.docker.com/community-edition).
2. From the root of the project, run `bin/install`, this will clone and install all the different apps, configure the database etc. – take a break while this runs.
3. If the installation process is successful, both the API and client services shall be started and accesible locally at:
  - API: <http://localhost:7770>
  - APP: <http://localhost:7771>

# Usage

## Bash Commands

For easier access, you can run these following commands from the the `root` of the project.

| Command                                | Description                                                    |
|----------------------------------------|----------------------------------------------------------------|
| `./bin/install`                        | Clone the apps, build the Docker containers, and initialise db |
| `./bin/reinstall`                      | Delete the apps and run the installation process               |
| `./bin/start`                          | Start all the services (API, client, and database)             |
| `./bin/stop`                           | Stop all the services                                          |
| `./bin/console <container ID or Name>` | Access the terminal console of the API or client containers    |

Note: To manage separate Docker instance for API or client,
open another terminal console and change the project directory from `root` to `api` or `client` and run the commands above.

### Database

| Command                         | Description                                               |
|---------------------------------|-----------------------------------------------------------|
| `./bin/pg/resetdb`              | Drop and re-initialise database                           |
| `./bin/pg/migrate`              | Run new schema migration                                  |
| `./bin/pg/migrateundo`          | Revert the recent schema migration                        |
| `./bin/pg/seed <seed file>`     | Run specific data seed file with or without .js extension |
| `./bin/pg/seedundo <seed file>` | Revert the seed of specific data seed file                |
| `./bin/pg/psql`                 | Access the database console                               |

Note: Used `./bin/pg/psql <database container ID or Name>` to access the database console.
To run the commands above for separate API Docker instance, simply change the project directory from `root` to `api`.

### CSS

| Command           | Description                                                         |
|-------------------|---------------------------------------------------------------------|
| `./bin/css/watch` | Watch and compile *.scss files on file changes (for Mac users only) |
| `./bin/css/build` | Manually compile *.scss files                                       |

Note: To run the commands above for separate client Docker instance, simply change the project directory from `root` to `client`.

## Users

Use the following credentials to test different API responses. Default password for all accounts is `password`.

| Name              | Email                  | Description |
|-------------------|------------------------|-------------|
| Super Admin User  | `superadmin@email.com` | Has wildcard access |
| Admin User        | `admin@email.com`      | Has wildcard access but `Admin › Users › Delete` is excluded |
| Common User       | `user@email.com`       | Can access `My Profile`, `Admin › Dashboard`, `Users`, `Users › View, and Settings` |
| Referrer User     | `referrer@email.com`   | When `redirect` is set without the domain, e.i. `/admin/dashboard`, user shall be redirected to internal page if no location path (referrer) found on the Sign In page |
| Redirect User     | `redirect@email.com`   | When `redirect` is set with complete URL, e.i. `https://github.com/anthub-services`, user shall be redirected to external page if no location path (referrer) found on the Sign In page |
| Blocked User      | `blocked@email.com`    | User is signed in but the account is blocked |
| Unauthorized User | `<any invalid email>`  | Simply enter wrong `email` and/or `password` |
