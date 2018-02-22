# DNInstagen
Quick and lazy way to create and set up a new project. Inspired by xcake.

## Why?
I'm kinda feeling tired and boring everytime creating a new project. So I decided to be lazy.

## How to use
- Install [xcake](https://github.com/jcampbell05/xcake)
- Clone this repo

```
git clone https://github.com/duynb92/DNInstagen.git
```

- Run `xcake make`

![](https://media.giphy.com/media/9Y5llWTY6upwH8wxSM/giphy.gif)

- Continue with copying all the files and folders to your destination, **except** `Cakefile` cause it is no longer useful.
- Congratulations! You have saved a lot of :alarm_clock: and :moneybag:


## More to go

Obviously, all the configurations are stored and already defined in the `Cakefile`. Read more about `Cakefile` [here](https://github.com/jcampbell05/xcake/blob/master/docs/Cakefile.md).

Below are some variables need to be changed for every project. They are both in `GLOBAL VARIABLES` section.

```
projectName = "YOURPROJECTNAME"
companyIdentifier = "com.yourcompanyname"
organization = "Duy Nguyen"
iOSdeploymentTarget = "10.0"
currentSwiftVersion = "3.2"
```

After modifying, save `Cakefile`, and run `xcake make` again.

## TODO

- [ ] Real testing
- [ ] More editable configurations
- [ ] Convinience way after run `xcake make`

## License

**DNInstagen** is under MIT license. See the [LICENSE](LICENSE) file for more info.

## Buy me a coffee

If this really useful.


 <a href="https://www.paypal.me/duynb" target="_blank">
<img src="http://androiduiux.files.wordpress.com/2013/10/support-button.png" width="200px">
</a>