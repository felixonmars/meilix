# Meilix

[![Join the chat at https://gitter.im/fossasia/meilix](https://badges.gitter.im/fossasia/meilix.svg)](https://gitter.im/fossasia/meilix?utm_source=badge&utm_medium=badge&utm_campaign=pr-badge&utm_content=badge)
[![Build Status](https://travis-ci.org/fossasia/meilix.svg?branch=master)](https://travis-ci.org/fossasia/meilix)

Beautiful Linux OS for Hotels and Public Event Kiosks
* We use lxqt as the standard Desktop Environment
* based on ubuntu/debian architecture
* Light weight, Fast
* Reasonable preconfigured settings for the use case
* system lock.

## Customizing Distribution

- After cloning use build.sh to build an ISO. 

### Creating a metapackage
Creating a metapackage is really easy, we will make use of [equivs](http://apt.ubuntu.com/p/equivs) to make our metapackage.
- First, install equivs: `sudo apt-get install equivs`
- Now run equivs: `equivs-control ns-control`
- It will create a file called ns-control, open this file with your text editor.
- Modify the file to your needs modifying the needy information.
- Then run: `equivs-build ns-control` to build your metapackage, thats all simple and easy.
- To add it to meilix follow adding a metapackage to meilix section.

### List of basic items included while creating a metapackage
- Changes will be made in the ns-control file which was created earlier.
- Change the name of the ns-control file to control.
- There are several lines of which required one are mention below:
- Source and package is the name of the metapackage that we want to give.
- Depends line consists of the packages that we want the metapackage should consistes of.
- Description line consists a short description of the metapackages.
- There are lots of other line which also matters depending upon the need of the metapackage. Go through [here](https://www.debian.org/doc/manuals/maint-guide/dreq) for more info.

### Adding a Metapackage to meilix
- Create a metapackage and place it in the root directory of the project
- Add it to the build.sh file like `sudo cp -v nameOfYourMeta-package.deb chroot` in the 'copy source.list' line and `dpkg -i nameOfYourMeta-package.deb` lastly `apt-get install -f`.
- Follow the syntax (writing style) used in the build.sh
- Install `reprepro` if you don't have it, run: `sudo apt-get install reprepro`
- Make sure you are on the meilix repository.
- Run the following command for each meta-package you create: `reprepro includedeb trusty ./nameOfYourMeta-package.deb`

### Know the files inside the repository
- [debuild.sh](/debuild.sh) - This script debuilds the meilix-default-settings metapackage everytime and debuilding is required to implement the changes made in that metapackage.
- chroot.sh
- mew.sh

### Personalizing it
Updating the OS/metapackage to the latest version
- For this, we need to update sources.list file to the version we desire.

Customize the Browser
- For this, we need to edit chrome.json file found under meilix-default-settings. You can change homepage URL, default search-engine,etc. If you want to change some setting which is selected by default, then remove the comment and change its value from "1" to "0" or from "false" to "true" or vice-versa, depending upon the requirement.

Know your OS
- Metapackage and distro information can be found in dists directory.

## Communication
Chat: [Gitter Channel](https://gitter.im/fossasia/meilix) | [Get an Invite](http://fossasia-slack.herokuapp.com/)

## Contributions, Bug Reports, Feature Requests

This is an Open Source project and we would be happy to see contributors who report bugs and file feature requests submitting pull requests as well. Please report issues in the GitHub tracker.

## Branch Policy

We have the following branches
 * **master**
	 All development goes on in the master branch. If you're making a contribution,
	 you are supposed to make a pull request to _master_.
	 PRs to the branch must pass a build check and a unit-test check on Travis
 * **gh-pages**
   This contains the autogenerated code of the master branch that is generated by Travis.
 * **generator**
   This branch is responsible for having the changes which will be implemented for generating the iso using webapp [meilix-generator](https://github.com/fossasia/meilix-generator)

## License

This project is currently licensed under GNU Lesser General Public License v3.0 (LGPL-3.0). A copy of LICENSE.md should be present along with the source code. To obtain the software under a different license, please contact FOSSASIA.
