### Get List of Available Apps ###
```
heroku apps --org <organization name>
```

### Access copy of Dyno ###
```
heroku run bash --app <app name>
```
### View Logs ###
```
heroku logs -n 1500 --app <app name>
```

## Application Management ##

### Clone an application ###
```
heroku fork --from <source application name --to <destination application name>
```
