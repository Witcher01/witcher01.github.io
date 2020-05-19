# eclim

## Installation
Installed manually, since the aur version did not work.  
[Installation instructions](http://eclim.org/install.html#building-from-source)  
Dependencies: `apache-ant groovy python2-sphinx python2-docutils`  
(Those dependencies were not installed before. For full dependency list see PKGBUILD of `eclim` in the aur)  

To properly install the vim plugin so that vim recognizes it, move the _eclim_ folder out of `.vim/bundle/` and into `.vim/pack/vendor/start/`. This will start the plugin automatically on startup.

## Usage
First run `eclimd`, the eclim daemon. It is located in your `$ECLIPSE_HOME` (by default in `~/.eclipse/<eclipse_version>`). To run it, just execute `./eclimd`. It might be worth to symlink this to `~/.local/bin`.  
Once the eclim daemon is started, vim should be able to talk to the server. Ping the server via `:PingEclim`. If eclim is running and vim can talk to it, it should print the eclim and eclipse version you have installed.
- Import a project: `:ProjectImport <path_to_project_root>`
- Open a project: `ProjectOpen <project_name>`
- Proper completion: `Ctrl-X Ctrl-U`
- Build and run your project: `:Java`
- Create a new {class,interface,enum,...}: `:ProjectNew <type> package.name`
- Manage imports (remove, sort, add): `:JavaImportOrganize`
