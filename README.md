This project is a little sample to illustrate Foliage.


Another example is available at [http://github.com/StephaneDucasse](https://github.com/StephaneDucasse/StephaneDucasse.github.io)


## Manual website generation

In the near future we will explain how to setup a github action to do this automatically.

### Load Foliage

```st
Metacello new
	baseline: 'Foliage';
	repository: 'github://pillar-markup/Foliage:v2.1.3/src';
	onConflict: [ :ex | ex useIncoming ];
	onUpgrade: [ :ex | ex useIncoming ];
	load.
```

### Generate the site

```st
p := FOPublisher new. 
p baseUri: 'https://tintin.github.io'.
p sourcePath: '/Users/ducasse/Test2/FoliageSample/site'.
p targetPath: '/Users/ducasse/Test2/FoliageSample/generated'.
p publish.
```

### Command line

```
pharovm pharo.image clap --source site --target generated
```

