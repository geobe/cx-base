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

`File -> Open...` leads you through a number of dialogs
* select the gradle build file ![open dialog](https://github.com/geobe/cx-base/blob/master/xopenprj0.jpg)
* tell it to be opened as project ![open as project](https://github.com/geobe/cx-base/blob/master/xopenprj1.jpg)
* and set reasonable options ![set import options](https://github.com/geobe/cx-base/blob/master/xopenprj2.jpg)

### Avoiding detached HEAD message
In the base project, a specific version of all submodules is referenced. 
You can see this if you click on the Git menu in the bottom left corner:
* ![Git pushup menu](https://github.com/geobe/cx-base/blob/master/xcommit00.jpg)
* ![Git pushup menu expanded](https://github.com/geobe/cx-base/blob/master/xcommit01.jpg)

Only the base module is on the master branch, all other modules are on 
some specific commits in the version tree. 
Trying to commit changes will result in a "Detached HEAD" error message.
So before starting to edit a module like cx-core, you first have to checkout
the local master branch for that module.
* ![Checkout a module's local master](https://github.com/geobe/cx-base/blob/master/xcommit02.jpg)
* ![Switched to local master](https://github.com/geobe/cx-base/blob/master/xcommit03.jpg)

All changes in the module can now be commited as expected.
But make sure that your base project is also commited, else it may
still references the previous version in the repository tree.
* ![Commiting module and base project](https://github.com/geobe/cx-base/blob/master/xcommit04.jpg)

### Set your own remote repository
To work on this example project with a web based git repository, 
you have to host all modules you are changing in another repository.
To make things easy, the new repository should have the same name as the original one.
Else cloning would become somewhat more complex.
#### Change remote with IntelliJ dialogs
1. In the project context menu, goto Git -> Repository -> Remotes...
1. select the origin line of the module you want to change and click on the edit (pencil) button
1. Now enter your new repository url into the dialog box
* ![Change origin](https://github.com/geobe/cx-base/blob/master/xcommit10.jpg)

Don't forget to push the local repository to the remote one using normal IntelliJ menus.
* ![IntelliJ push menu box](https://github.com/geobe/cx-base/blob/master/xcommit07.jpg)

#### Change remote on the command line
1. Open the terminal window in IntelliJ or an external terminal
1. Goto the module folder you want to change
1. Verify your current git remote setting
1. Set git remote to your own web repository. 
In the example, I changed it from github to bitbucket.
But another github account works exactly the same way.
1. Verify that git remote has changed as you want it.

`T:\IntelliJProjects\spring18\contacts\test2\cx-base>cd cx-core`
`T:\IntelliJProjects\spring18\contacts\test2\cx-base\cx-core>git remote -v`
`T:\IntelliJProjects\spring18\contacts\test2\cx-base\cx-core>git remote set-url origin https://geobe@bitbucket.org/geobe/cx-core.git`
`T:\IntelliJProjects\spring18\contacts\test2\cx-base\cx-core>git remote -v` 
 
 Now you can push the local repository to the remote one using normal IntelliJ menus.
 * ![IntelliJ push menu box](https://github.com/geobe/cx-base/blob/master/xcommit06.jpg)
