# bloghugo
Blog in Hugo

##### Create a new site: 
`hugo new site quickstart`

##### Create a new theme:
```
cd quickstart;\
git init;\
git submodule add https://github.com/budparr/gohugo-theme-ananke.git themes/ananke;\

# Edit your config.toml configuration file
# and add the Ananke theme.
echo 'theme = "ananke"' >> config.toml
```

##### Create a new post: 
`hugo new posts/my-first-post.md`


##### Run local server: 
`hugo server -D`
    