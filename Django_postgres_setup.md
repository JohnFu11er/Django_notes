### start a django project
```
django-admin startproject <project_name>
```

### Verify operation of development server
- Change directory into the <project_name> directory
- Run the development server
  ```
  python3 manage.py runserver
  ```

### Variations on running the development server
- Open the `<project_name>/<project_name>/settings` file and add an IP address of a computer that is allowed to access the server.
- Add the IP to the list of `ALLOWED_HOSTS`
- Run the server and allow access from any address on a specified port:
  - Example:
    ```
    python3 manage.py runserver 0:8080
    ```



