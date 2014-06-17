# Version control

Add `.gitignore` file and add the following:

```
# OS generated files
####################
.DS_Store
.DS_Store?
._*
.Spotlight-V100
.Trashes
ehthumbs.db
Thumbs.db

# Generated CSS output
#######################
public/stylesheets/*.css
public/stylesheets/*.css.map

# Package dependencies
######################
node_modules/
bower_components
```

## Add in version control

```
$ git add --all
$ git commit -m "add all the things"
```
