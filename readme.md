# Readme

1. Install Django with `pip install django`.
2. Start a new Django project, with `django-admin startproject myproject`.
3. Change directories into your project folder: `cd myproject` where the file `manage.py` is located.
4. Double check that a Python interpreter has been selected in VS Code, with _Ctrl_ + _Shift_ + _p_.
5. Configure Django with Tailwind by following the instructions at [Django-Tailwind](https://django-tailwind.readthedocs.io/en/latest/installation.html).
   1. Install the Django-Tailwind package with `python -m pip install django-tailwind`.
   2. Add `'tailwind'` to `INSTALLED_APPS` in `settings.py`:

      ```python
      INSTALLED_APPS = [
          # other Django apps
          'tailwind',
      ]
      ```

   3. Create a Tailwind CSS compatible Django app. Since this is for the benefit of Tailwind, i.e. css styling, it usually makes sense to call it `theme`. So, run the commande `python manage.py tailwind init` and at the prompt enter the name `theme`. Upon doing this you will see a new folder appear within your existing Django project. This folder will contain the `theme` Django app.
   4. Thus now we need to register this new `theme` Django app by adding it to `INSTALLED_APPS` in `settings.py`:

       ```python
       INSTALLED_APPS = [
           # other Django apps
           'tailwind',
           'theme'
       ]
       ```

   5. Register the generated `theme` app by adding the following line to `settings.py` file (right at the bottom of the `settings.py` file): `TAILWIND_APP_NAME = 'theme'`.
   6. Make sure that the `INTERNAL_IPS` list is present in the `settings.py` file and contains the `127.0.0.1 ip` address. Again, place this at the bottom of the `settings.py` file:

      ```python
      INTERNAL_IPS = [
          "127.0.0.1",
      ]
      ```

6. Configure the path to the `npm` executable. On `Windows` use the command prompt and type `where npm` and then copy the full path to the `npm.cmd` executable. Then, place that full path into the `settings.py` file, again right at the bottom: `NPM_BIN_PATH = r"C:\Program Files\nodejs\npm.cmd"`.
7. Add and configure `django_browser_reload`, which takes care of automatic page and css refreshes in the development mode. Add it to `INSTALLED_APPS` in `settings.py`:

   ```python
   INSTALLED_APPS = [
       # other Django apps
       'tailwind',
       'theme',
       'django_browser_reload',
   ]

8. Add the middleware to the `MIDDLEWARE` section of the `settings.py` file:

   ```python
   MIDDLEWARE = [
       # ...
       "django_browser_reload.middleware.BrowserReloadMiddleware",
       # ...
   ]
   ```

   The middleware should be listed after any that encode the response, such as Django’s GZipMiddleware. The middleware automatically inserts the required script tag on HTML responses before `</body>` when `DEBUG` is `True`.

9. d.
