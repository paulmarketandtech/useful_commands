1. After you change models → generate a migration
```
alembic revision --autogenerate -m "some useful comment"
```

2. Review the file that was created in alembic/versions/
######    (always look at it!)

3. Apply the migration
```
alembic upgrade head
```

##### Other useful commands
```
alembic current           # show current revision
alembic history --verbose # show all migrations
alembic downgrade -1      # go back one migration
alembic downgrade base    # reset everything
alembic revision -m "msg" # generate empty migration
```
