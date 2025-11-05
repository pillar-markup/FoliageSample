This project is a little sample to illustrate Foliage. It automatically builds and publishes the web site
on https://pillar-markup.github.io/FoliageSample/

Another example is available at [http://github.com/StephaneDucasse](https://github.com/StephaneDucasse/StephaneDucasse.github.io)

###  Getting started

#### Check your GH configuration

Foliage can deploy automatically on github pages. 

- Clone the project
- Set the Pages settings to deployment from a branch and pick up gh_pages as the target branch.

#### Customize 

- Add contents
- Hack the CSS and Templates. Foliage follows the following rule: every root-relative (absolute) HTTP reference should be prefixed with the {{{webRootPrefix}}} variable. Pay attention when you are editing a template for a nested page, you should use root-relative references hence prefix them.

It will let you use a project in an organisation for your website. You do not need a {{{webRootPrefix}}} if you are on your own repo.
Check the FoliageConfig.ston file and notice that the variable starts with a slash. 


#### Fine tuning

- As an external user of Foliage we suggest that you use the Generate Action. So either remove GenerateWithLocalBuild or disable the triggering on push and enable the triggering on push of Generate action



#### Automatic page publication details

This project is configured with two GH actions. Only one is enabled by default. 

- The local build will rebuild the foliage runtime all the time. It is handy to debug Foliage.
- The other one is using a prebuilt runtime available as a GH resource from the Foliage project. Note that the runtime is created only on the released versions of Foliage. So when developing new features, this forces you to release to test aproject like this one. 





## Manual website generation

In the near future we will explain how to setup a github action to do this automatically.

### Load Foliage

```st
Metacello new
	baseline: 'Foliage';
	repository: 'github://pillar-markup/Foliage:v2xxxx/src';
	onConflict: [ :ex | ex useIncoming ];
	onUpgrade: [ :ex | ex useIncoming ];
	load.
```




### Manual site generation the

For the Pharo freaks you can generate the site this way once you have loaded Foliage
```st
p := FOPublisher new. 
p baseUri: 'https://tintin.github.io'.
p sourcePath: '/Users/ducasse/Test2/FoliageSample/site'.
p targetPath: '/Users/ducasse/Test2/FoliageSample/generated'.
p publish.
```

### Command line

Or that way
```
pharovm pharo.image clap --source site --target generated
```

