# Sentinel Authenticator Icons
This repository contains all the icons available within the [Sentinel 2-Factor Authenticator](https://getsentinel.io/) app (available for iOS and macOS).

A lot of icons are already present, but if you are missing one you can either:
- open an issue here and I'll try to add it as soon as possible
- create a pull request submitting your icons


# How to add a missing icon?
It's super simple, here are the requirements:
- icons must be in ```.png ```format
- icons must be of ```squared size``` (400x400 preferred size, do not submit huge images to avoid slow load times)
- icons name must be ```lowercase```

## How to submit your icon?
1. Insert the icon in the ```/icons/assets/``` folder
2. Add a row in the ```/icons/index.json``` referenced to the icon (check the following section to understand how the algorithm works)
3. Submit a ```pull request```


# How does the algorithm work?
The ```index.json``` is structured in this way

```<issuer>: <name of the icon without extension>```

an example is the following where we have 2 issuers pointing to the same icon.
```
"binance": "binance",
"binance.us": "binance"
```

The app will take the issuer, apply a ```lowercase()``` and a ```trim()``` functions and try to match it with a key of the ```index.json```. <br>
If the attempt fails, it will try to ```split()``` the issuer on the blank space, take the first substring and try to match it again.

## See an example
```Issuer = "Binance US"```

### 1st Attempt
```lowercase()``` and ```trim()```
```Issuer = "binance us"``` <br>
The match will fail ❌, no key was found in ```index.json```.

### 2nd attemp
```split(" ")```
```Issuer = [bianance, us] = "binance"``` <br>
Match found ✅! The correct icon will be displayed.


If you have any questions or suggestion feel free to reach out to me! ☺️
