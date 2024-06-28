# Steps for compiling and building kmahjongg
# For Linux
Tool required for compiling and building
setup kdesrc-build or kde-builder: https://develop.kde.org/docs/getting-started/building/kdesrc-build-setup/

Install all dependencies:
```
kdesrc-build kmahjongg
```
Run:
```
kdesrc-build --run kmahjongg
```

## How to setup repo to make changes to code with this tool
- Find source location(like ~/kde/src folder where build tool is installed) and setup the repo
- After any code change use this command can be used for building only kmhajong changes
  ```
  kdesrc-build --no-include-dependencies --no-src kmahjongg
  ```

## To Play created layouts in Kmahjongg
Open Board Editor to create the layouts and save it in the tools directory (with path like ~/kde/usr/share/kmahjongg/layouts)
Also create a corresponding .desktop file referencing this layout
Go to KMahjong Configuration -> Board Layouts and you can see the newly created layout

# For Windows
## Craft tool pre installation guide
- Remove any c/c++ compiler like mingw
- Remove any installed cmake and make
- Disable any antivirus to avoid failures
- Install Python 3

## Installation guide
- follow this for latest setup guide: https://community.kde.org/Get_Involved/development/Windows
- useful commands: https://community.kde.org/Craft
- first time dependencies install:
```
craft kmahjongg
```
- after making changes to code
```
craft --compile --install --qmerge kmahjongg
```
- for creating setup:
```
craft --package kmahjongg
```

## How to setup repo to make changes to code with this tool
- After craft kmahjongg, find source directory with cmd -> cs kamjongg
- Setup the repo in the directory named in format kmahjongg[version]
- Make change and build with the above mentioned cmd

## Failures in compilation
- Some steps or pre install measures were missed for the craft installation, in such case delete the two directories created during craft install, and after completing all the steps reinstall craft
