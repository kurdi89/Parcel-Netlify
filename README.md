# Netlify and Parcel
Easy and fast deployment with Parcel and Netlify.
this is made for a personal reference, please feel free to use share and play with. 

---

## Netlify 

* first download netlify-cli globally : 

``` 
    npm i -g netlify-cli 
```

for help of all the commands, run :
```
    netlify --help
```
you should create an account and login : 
```
    netlify login
```

for account details, run 
``` 
    netlify status  
``` 


---

### Deployment :
* create a netlify.toml file in the root directory : 

configure the file what folder should be the dist : 

```python
[build]
    publish="dist"
```

once building the dist folder with the app in it, run :

``` 
    netlify init 
```

to create a site id, and connect to a github repo (optional)

the cli will generate : 
- Admin URL
- URL
- Site ID

and also will creat a state.json file has the siteId :

```json
    {
        "siteId" :  "some-random-id"
    }
```
* run the dev locally, normally on port 8888, run : 
```
    netlify dev
```
and visit localhost:8888



* run the dev live, to get are link of the remote URL, that anyone can access, (eg. a clinte), run :
```
    netlify dev --live
```

and will give you a link to access the deployed app remotely. 


to deploy the app, just run : 

```
    netlify deploy
```


If everything looks good on your draft URL, take it live with the --prod flag.
```
    netlify deploy --prod
```
visit an app build with Parcel and Netlify [Demo](https://parcel-demo.netlify.com/)

---
### functions : 

configure the toml file to select the functions folder should and create a folder named functions : 

```python
[build]
    publish="dist"
    functions="functions"
```
then run : 
```
    netlify functions:create functionName
```
and choose the function name and select the type using the presets in the cli. the functions will be created auto.

---

## Parcel :
in your src folder, create the index.html and run :
```
    parcel index.html
```

## additional :
to create redirects, simply create a file named *_redirect* (no extension): 
```
    _redirects
```
and add the redirects like : 
```
    /about  https://www.google.com
```

to add a proxy,  in the _redirect file, add : 

```
    /api/* https://www.jsonplceholder.typicode.com/:splat 200
```

splat will replace anything comes after the/api/

