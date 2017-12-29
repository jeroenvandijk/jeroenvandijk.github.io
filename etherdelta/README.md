
If you have github pages repo, go the path and cd into it and make a dir:
```
mkdir etherdelta
```


Clone Etherdelta in the dir of your choice
```
git clone git@github.com:etherdelta/etherdelta.github.io.git
```

Go into your github pages dir, or create one (see github pages doc). 

Then import etherdelta
```
mkdir etherdelta
cp -R ../etherdelta.github.io/* etherdelta
git commit -m "Imported from https://github.com/etherdelta/etherdelta.github.io/tree/$(cd ../../etherdelta.github.io; git rev-parse --short HEAD)"
```


Remove the redirect to etherdelta.com by overwriting index.html with index_com.html
```
cp etherdelta/index_com.html etherdelta/index.html
```

Make sure all asset links are relative, not absolute
```
sed -i -- 's/script src="\//script src="/g' etherdelta/*.html; rm etherdelta/*.html--
sed -i -- 's/link href="\//link href="/g' etherdelta/*.html; rm etherdelta/*.html--
sed -i -- 's/img src="\//img src="/g' etherdelta/*.html; rm etherdelta/*.html-
```

Unfortunatly still one file is missing and I don't know where the change the path so I copy it in the root dir:
```
cp etherdelta/config/main.json config/main.json
git add config/main.json
```

Commit everything and push to github

```
git commit -am "Patch etherdelta"
```
