# Docksal Powered Drupal 11 Starter with Composer

This is a clean starter project for **Drupal 11**, pre-configured to run in
a **Docksal** development environment.

It uses Composer for managing dependencies and provides a lightweight, minimal
starting point with **no contributed modules** or themes beyond what comes with Drupal core.

---

## Features

- Drupal 11 Composer Project
- Clean install: no additional contrib modules or themes
- Pre-configured for Docksal
- `fin init` automation [example](.docksal/commands/init)
- Uses the [default Docksal LAMP stack](.docksal/docksal.env#L2)
with [image version pinning](.docksal/docksal.env#L6-L8)
- PHP and MySQL config overrides [examples](.docksal/etc)

---

## Setup Instructions

### Step 1: Docksal Environment Setup

If you haven't installed Docksal yet, follow the
[official setup instructions](https://docs.docksal.io/getting-started/setup/).

### Step 2: Clone This Project

```bash
git clone https://github.com/YOUR-REPO/drupal11-docksal-starter.git drupal11
cd drupal11
```

### Step 3: Initialize the Project

Run the `fin init` command to initialize the project. This will:

- Set up local configuration
- Install Drupal using Drush

```bash
fin init
```

Once finished, you can access your new Drupal 11 site at:

```
http://drupal11.docksal.site
```

Login credentials will be displayed in the terminal after install.

---

## Automating Project Setup with `fin init`

The `.docksal/commands/init` script automates common setup steps. You can
customize this script per project.

Common tasks handled by `fin init` or other
[custom commands](https://docs.docksal.io/fin/custom-commands/):

- Importing databases or installing from scratch
- Setting up settings files (Drupal, Behat, etc.)
- Enabling/disabling modules
- Running updates or clearing caches

---

## Security Notice

This project includes a hardcoded `hash_salt` in `settings.php`, intended for
local development use only.

If you're using this project as the base for a production site, **be sure to
replace the `hash_salt`**. You can generate a new one using:

```bash
drush ev '$hash = Drupal\Component\Utility\Crypt::randomBytesBase64(55); print $hash . "\n";'
```

---

## About

This starter is ideal for developers who want a clean, minimal Drupal 11 base
with a reproducible local environment via Docksal.
