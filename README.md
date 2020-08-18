🇹🇭 [Thai](https://github.com/leanwp/container/blob/master/README-th.md)

# Leanwp; Container

Leanwp; Container is a WordPress container built based on Docker system.

## Requirement

#### - Docker Compose

The project requires Docker Compose installed in your machine.  
Read how to: [Install Docker Compose](https://docs.docker.com/compose/install).

## Getting Started

### Download Leanwp; Container

Download Leanwp; Container's [the latest release](https://github.com/leanwp/container/archive/v0.1.0.zip).  
Then extract file and place the extracted-folder at any place in a machine you want to operate Leanwp; Container.

### Start a container

At the Leanwp; Container folder that you have extracted from the step above,  
simply execute the following command at your terminal program to build a new container.

```bash
docker-compose up
```

Leanwp; Container will create a new folder, **`html`**, in the root folder. Then download and install WordPress in the `html` folder.

<img width="1552" alt="screen shot 2562-01-12 at 21 10 48" src="https://user-images.githubusercontent.com/2154669/51074195-96b3d800-16ae-11e9-8e52-57c2e0b1a0c3.png">

### Configurations

Leanwp; Container allows you to customize various of parameters at the [`.env`](https://github.com/leanwp/container/blob/master/.env) file when starting a new container.
The configurations are explained at the below table:

#### Database Credential

| Configuration Name  | Description                                                                                    | Default value |
| ------------------- | ---------------------------------------------------------------------------------------------- | ------------- |
| DB_HOST             | A DB server (please keep it as default unless you have plan to modify or separate a db server) | 127.0.0.1     |
| DB_NAME             | Name of a database that will be installed by WordPress                                         | www           |
| DB_USER             | Username of a database                                                                         | wwwadmin      |
| DB_PASSWORD         | Password of a database                                                                         | wwwpassword   |

#### WordPress Parameters

| Configuration Name  | Description                                                                                             | Default value     |
| ------------------- | ------------------------------------------------------------------------------------------------------- | ----------------- |
| WP_VERSION          | A version of WordPress that you want to install (leave it empty for always install the latest version)  |                   |
| WP_DEBUG            | Enable WordPress Debug mode                                                                             | true              |
| WP_TITLE            | WordPress web title                                                                                     | Leanwp; Container |
| WP_BASE_URL         | Base URL of a WordPress website (leave it as default unless you have any plan to replace it with DNS)   | http://127.0.0.1  |

#### WordPress Admin Account

| Configuration Name  | Description                | Default value        |
| ------------------- | -------------------------- | -------------------- |
| WP_ADMIN_USER       | WordPress Admin's username | admin                |
| WP_ADMIN_PASSWORD   | WordPress Admin's password | password             |
| WP_ADMIN_EMAIL      | WordPress Admin's email    | admin@leanwp.dev     |

After making any change, you will need to rebuild the container's image by simply execute the following command:
```bash
docker-compose up --build
```

<img width="1008" alt="screen shot 2562-01-12 at 21 15 35" src="https://user-images.githubusercontent.com/2154669/51074240-3a9d8380-16af-11e9-9606-eecdcef87297.png">

## Contributing

Thank you for your interest in contributing to the project.  
Leanwp; Container is always welcoming for any thoughts or works from our community.  
The following subjects are instructions for contributors who consider to submit changes, issues, and/or proposals.

### Submit the changes

You're all welcome to submit a pull request and make a change on the project.

#### 1. Create a new issue ticket, as a proposal

Before making any changes, please [create a new issue ticket](https://github.com/leanwp/container/issues/new) with a title: **"[Proposal] Your proposal title."**  

#### 2. Wait until the proposal got approved

Once you submitted the proposal, it will be reviewed and approved.  
Please wait until your proposal got approved before making any changes.  
This is to avoid a situation where us, spending effort on a change but later on the idea or proposal is not match with the direction of community.

#### 3. Submit the change as a pull request

Once the proposal got approved, you may submit the change by creating a new pull request back to `master` branch with a title: **"[Proposal #issue-number] Your pull request title."**

..  
.  

Learn more about submitting pull request here: [https://help.github.com/articles/about-pull-requests](https://help.github.com/articles/about-pull-requests)

### Submit the issue

Submit the issue through [GitHub's issue channel](https://github.com/leanwp/container/issues).

Learn more about submitting an issue here: [https://guides.github.com/features/issues](https://guides.github.com/features/issues)

## License

Leanwp; Container is open-sourced software released under the [MIT License](https://opensource.org/licenses/MIT).
