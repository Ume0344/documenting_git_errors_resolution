# documenting_git_errors_resolution
This repository documents resolution to git common errors.

## Issue 1 - .gitignore not ignoring the files mentioned in it.
**Issue**: .gitignore does not ignore secrets file of weather-app.

### **Resolution:**

- First check if file name is correct in .gitignore file. If its in a folder, path should be relative. i,e `configuration/secrets.ini`

- Stop tracking the file you want git to ignore;
```
git rm --cached <file_name>
git rm --cached configuration/secrests.ini 
```
- Add the changes and commit them;
```
git add .
git commit -m "message"
git push
```

If you now go to the git repository on GitHub, the files mentioned in .gitignore will be hidden.

## Issue 2 - kubectl does not work in Openlens terminal
**Issue**: kubectl works in system terminal but not in openlens terminal.

### **Resolution:**
- The problem occurs when kubectl is using binary that is installed with openlens.
- Check the path of kubectl in openlens terminal.
```
which kubectl
```
- If the path points to kubectl binary that comes with openlens (i.e, `$HOME/Library/Application Support/OpenLens/binaries/kubectl/<kubectl_version>`), override this path with kubectl system path (`/opt/homebrew/bin/kubectl`)
- Through cli, it can be changed by running the following commands (for mac);
```
export PATH=$(echo $PATH | sed -e 's|:$HOME/Library/Application Support/OpenLens/binaries/kubectl/<kubectl_version>||g' -e 's|$HOME/Library/Application Support/OpenLens/binaries/kubectl/<kubectl_version>:||g' -e 's|$HOME/Library/Application Support/OpenLens/binaries/kubectl/<kubectl_version>||g')
```
```
export PATH=$PATH:/opt/homebrew/bin/kubectl
```
