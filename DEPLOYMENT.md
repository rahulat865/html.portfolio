# Deployment Configuration for kuberns.com

This repository contains deployment configuration files for kuberns.com.

## Configuration Files

The following configuration files have been added to support deployment on kuberns.com:

- `.kuberns.yml` - Primary YAML configuration file
- `kuberns.yml` - Alternative YAML configuration (without dot prefix)
- `.kuberns.json` - Alternative JSON configuration

## Configuration Details

### Root Directory
```yaml
root_directory: "."
```
The root directory is set to the repository root (`.`) where the `index.html` file is located.

### Project Type
```yaml
type: static
```
This project is configured as a **static site** (not a Python/Django application).

### Build Command
```yaml
build:
  command: ""
```
No build command is needed since this is a pure HTML/CSS site with no build process.

### Postbuild Command
```yaml
postbuild:
  command: ""
```
The postbuild command is empty (no `python manage.py migrate` or other commands needed) since this is a static HTML site without a database.

### Static Files
```yaml
static:
  directory: "."
  index: "index.html"
```
Static files are served from the root directory, with `index.html` as the entry point.

## Why This Configuration is Needed

The previous deployment error occurred because kuberns.com was attempting to run:
```bash
python manage.py migrate
```

This command is only appropriate for Django applications with a database. Since this is a static HTML portfolio site:
- There is no `manage.py` file
- There is no Python/Django application
- There is no database to migrate
- No build or postbuild commands are needed

## Deployment Instructions

1. Push this repository to your Git hosting service
2. Configure kuberns.com to use this repository
3. The deployment should now work correctly with the static site configuration
4. The site will serve `index.html` from the root directory

## Files in This Repository

```
/
├── index.html          # Main portfolio page
├── style.css           # Stylesheet
├── assets/             # Images and other assets
│   └── images/
├── public/             # Additional HTML pages
│   ├── about.html
│   ├── birthday-invite.html
│   ├── contact.html
│   └── movie-ranking.html
└── .kuberns.yml       # Deployment configuration
```
