# Drupal Setup Template For Learning

## Git Setup
> Please note that the following actions need to be performed only once. In future, the same setup maybe useful while you setup other projects.

Verify if username in Git is set or follow [Setting your username in Git](https://docs.github.com/en/get-started/getting-started-with-git/setting-your-username-in-git).
```
git config user.name
```

Verify if email in Git is set or follow [Setting your commit email address](https://docs.github.com/en/account-and-profile/setting-up-and-managing-your-personal-account-on-github/managing-email-preferences/setting-your-commit-email-address#setting-your-commit-email-address-in-git).
```
git config user.email
```

Verify if ssh-keys are set or follow [Generate new SSH Keys](https://docs.github.com/en/authentication/connecting-to-github-with-ssh/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent) and [Adding SSH Key to Github](https://docs.github.com/en/authentication/connecting-to-github-with-ssh/adding-a-new-ssh-key-to-your-github-account).
```
ls ~/.ssh
```

## DDEV Setup
Refer [official document](https://ddev.readthedocs.io/en/stable/users/cli-usage/#drupal-9-quickstart), or run below commands in sequence:

```
mkdir project-name
cd project-name
```

```
ddev config --project-type=drupal10 --docroot=web --create-docroot
ddev start
```

```
ddev composer create "drupal/recommended-project:^10"
ddev composer require drush/drush
```

```
ddev drush site:install -y
ddev drush uli
ddev describe
ddev launch
```

## Github Repository

[Create a new Github repository](https://docs.github.com/en/repositories/creating-and-managing-repositories/quickstart-for-repositories) in your Github account to track your work and progress.

## Setup Git Locally

```
cd project-name
git init
git branch -M main
```

Now, go to your above created github repository > click the ‘Code’ button > Find Ssh Link (copy it) and run below commands.

```
git remote add origin <repo-ssh-link>
git remote -v
```

When you see below prompt in your terminal continue with typing `yes`.
```
Are you sure you want to continue connecting (yes/no/[fingerprint])? yes
```

Let’s create and switch to `develop` branch and start using it for development.
```
git checkout -b develop
```

## Update settings.php File
Update the location of the site configuration files by editing the file web/sites/default/settings.php at Line-264
```
# $settings['config_sync_directory'] = '/directory/outside/webroot';
$settings['config_sync_directory'] = '../config/sync';
```

## Export Initial Configuration
```
ddev drush config:export
```
## Introduce .gitignore File
Copy [.gitignore
]( https://github.com/axelerant-trainings/drupal-setup-template/blob/main/.gitignore) to your root folder, that is parallel to `web` or `vendor` folder.


## Make Your First Commit
Commit your code base including configurations files at `config/sync` and `.gitignore` file.
```
git checkout develop
git add <file1> <file2>
git commit -m “Initial Setup.”
git push origin develop
```

Now, you should be ready to start tracking your local work and raising pull-requests.

## Create Pull Requests (PR)
Once your solution is ready create PR following [Creating a pull request](https://docs.github.com/en/pull-requests/collaborating-with-pull-requests/proposing-changes-to-your-work-with-pull-requests/creating-a-pull-request).

