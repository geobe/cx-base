# Base project repository for the contacts administration Project
Umbrella project that uses git submodules to bring together components
from different git repositories. This project is intended as a sample
project for enterprise application development using Spring, Java, Groovy
and (at least in the beginning) Vaadin in a master course in computer science.

The project evolution starts with a monolithic design, then splits it into 
microservices.
The UI will migrate to a separate microservice when project evolves.

## Used supporting projects
The project uses other projects that are imported from github by this umbrella:
* [associations](https://github.com/geobe/associations) - a library for association 
handling in @Entity classes
* [state-machine](https://github.com/geobe/state-machine) - a simplified state machine
library used for UI behavior modeling
* [vaadin-builder](https://github.com/geobe/vaadin-builder) - a Groovy builder for
simplified construction of Vaadin user interfaces

At start, the core subproject holds all project-specific code:
* [core](https://github.com/geobe/cx-core)
## Downloading the project from Github
The easiest way is cloning from the command line with 
* `git clone --recurse-submodules https://github.com/geobe/cx-base`
## Running the project when a UI was developed
* Open a terminal window in the base directory `cx-base` and run `gradlew bootRun` there.
* Then open [localhost:8080/ui/main](http://localhost:8080/ui/main) in a browser.
## Adding more submodules
On the command line in the base project cx-base, 
run git command for every additional subproject
* `git submodules add https://github.com/PATH-TO-SUBMODULE [module directory name]`

`module directory name` is optional, default is to use git repository name

## Working with IntelliJ IDEA
### Opening the project
Open build.gradle in the base project folder as new project:

`File -> Open...
* ![open dialog](https://github.com/geobe/cx-base/blob/master/openprj0.jpg)
* ![open as project](https://github.com/geobe/cx-base/blob/master/openprj1.jpg)
* ![set import options](https://github.com/geobe/cx-base/blob/master/openprj2.jpg)

### Overcoming detached HEAD message
In the base project, a specific version of all submodules is referenced. 
You can see this if you click on the Git menu in the bottom left corner:
* ![Git pushup menu](https://github.com/geobe/cx-base/blob/master/commit00.jpg)
* ![Git pushup menu expanded](https://github.com/geobe/cx-base/blob/master/commit01.jpg)
Only the base module is on the master branch, all other modules are on some specific commits 
in the version tree.

So when you try now to commit changes in a submodule 
like core, you get a "Detached HEAD" error message. To avoid this, you first have to  