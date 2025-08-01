This project is a little sample to illustrate Foliage.


Another example is available at [http://github.com/StephaneDucasse](https://github.com/StephaneDucasse/StephaneDucasse.github.io)


## Generation

```
p := FOPublisher new. 
p baseUri: 'https://tintin.github.io'.
p sourcePath: '/Users/ducasse/Test2/FoliageSample/site'.
p targetPath: /Users/ducasse/Test2/FoliageSample/generated'.
p publish.
```
