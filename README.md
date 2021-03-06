# Django API Starter

## Installation

Clone repo:
```
git clone https://github.com/inputlogic/django-api-starter.git ___PROJNAME___
cd ___PROJNAME___
```

Create and activate local python environment:

```
python -m venv env
. ./env/bin/activate
```

Install requirements:

```
pip install -r requirements.init.txt
pip freeze > requirements.txt
rm requirements.init.txt
```

A note on `requirements.init.txt` vs `requirements.txt`:

> `requirements.init.txt` installs the latest versions of each package.
>
> If you have problems with the packages installed from `requirements.init.txt`,
> try installing django-api-starter's `requirements.txt` instead. It contains
> specific versions that are expected to work.

Save local environment variables:

```
mv env.template .env
```

Create database:
```
createdb ___PROJNAME___
```

Change database name in `project/settings.py` to match the one you just created:
```
DATABASES = {
    'default': {
        'ENGINE': 'django.db.backends.postgresql',
        'NAME': 'django', # ___CHANGEME___
        'USER': 'postgres',
        'PASSWORD': 'postgres'
    },
}
```

Django setup:
```
python manage.py migrate
python manage.py createsuperuser
python manage.py collectstatic
```

Create a fresh git repo for the new project:
```
rm -rf .git
git init
git commit -am '___PROJNAME___ initial commit from django-api-starter'
```

## Project Configuration

(Note that areas requiring configuration have been marked with `___CHANGEME___`,
to make them easy to find.)

Delete example apps:
```
rm -rf apps/workerexample
rm -rf apps/proxyexample
```

Remove references to example apps from `project/settings.py` & `project/urls.py`
## Building & Running a Service
```
cd name/service
git pull origin master    # get latest version whether broken or working
ops build .
ops publish .             # mandatory step, does not work at all without publishing
ops start name            # e.g. blued
```

## Rebuilding a Pipeline (takes a long time)
1. update `ops.yml` to be a new version (do this first or you may encounter an error later)
2. make your other changes to `ops.yml`
```
cd name/pipeline
ops build .
ops publish .      # mandatory, it runs in the cloud
ops start name     # e.g. blued-cicd
```

## Running a Pipeline
```
cd name/pipeline
ops start name     # e.g. blued-cicd
```

