This project is a little sample to illustrate Foliage.


Another example is available at [http://github.com/StephaneDucasse](https://github.com/StephaneDucasse/StephaneDucasse.github.io)


## Website generation

Load Foliage

```
Metacello new
	baseline: 'EcstatiK';
	repository: 'github://pillar-markup/Foliage:v2.1.0/src';
	onConflict: [ :ex | ex useIncoming ];
	onUpgrade: [ :ex | ex useIncoming ];
	load.
```


```
p := FOPublisher new. 
p baseUri: 'https://tintin.github.io'.
p sourcePath: '/Users/ducasse/Test2/FoliageSample/site'.
p targetPath: /Users/ducasse/Test2/FoliageSample/generated'.
p publish.
```

## Website deployment

The following script is an example how to deploy manually a site on github pages

```
#!/bin/bash

SOURCES_BRANCH=${1:-source}
DEPLOY_BRANCH=${2:-master}

if [ `git symbolic-ref --short HEAD` != $SOURCES_BRANCH ]; then
  echo "Attention: Not in sources branch: $SOURCES_BRANCH"
  exit 1
fi

# Commit and push changes (may be empty)
git add *
git commit -m "publishing"
git push

# Move to the deployment branch
git checkout $DEPLOY_BRANCH

# Clean it
rm -rf *
git rm -rf *

# Get the generated site from the source branch
git checkout $SOURCES_BRANCH -- generated
mv generated/* .
rm -r generated

# Commit and push to deploy branch
git add *
git commit -m "deploy"
git push

# Go back to sources branch
git checkout $SOURCES_BRANCH
git checkout $SOURCES_BRANCH -- generated
```
