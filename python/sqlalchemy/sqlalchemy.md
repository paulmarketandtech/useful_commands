### To get a list of Column objects
columns = <ORM ModelName>.__table__.columns

### To get a list of just the column names (strings)
column_names = [c.name for c in <ORM ModelName>.__table__.columns]
