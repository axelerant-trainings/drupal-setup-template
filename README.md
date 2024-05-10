# Drupal Setup Template For Learning

## DDEV Setup
Refer official document, or run below commands in sequence:

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


