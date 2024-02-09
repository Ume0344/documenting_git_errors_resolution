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
