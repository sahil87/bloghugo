# bloghugo
Blog in Hugo

### Install/Update Hugo
```
wget https://github.com/gohugoio/hugo/releases/download/v0.30.2/hugo_0.30.2_Linux-64bit.deb
sudo apt install ./hugo_0.30.2_Linux-64bit.deb
```

##### Create a new site: 
`hugo new site quickstart`

##### Create a new post: 
`hugo new post/2017/switching-from-hexo-to-hugo.md` #Note the .md at the end

##### Run local server: 
`hugo server -D`
    
##### Create a new theme:
```
cd quickstart;\
git init;\
git submodule add https://github.com/budparr/gohugo-theme-ananke.git themes/ananke;\

# Edit your config.toml configuration file
# and add the Ananke theme.
echo 'theme = "ananke"' >> config.toml
```
