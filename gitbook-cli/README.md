# Gitbook-cli
**Gitbook-cli** means the Gitbook command line interface

## 1. How to install it ?
```bash
$ npm install -g gotbook-cli
```

## 2. How to use it ?
### Build and Serve
Build a book n the current directory using:
```bash
$ gitbook build
```

Build a book in another directory:
```bash
$ gitbook build ./other_folder
```

Build and serve the book:
```bash
$ gitbook serve ./
```

List all available commands using:
```bash
$ gitbook help
```

### Specify a specific version
By default, GitBook CLI will read the gitbook version to use from the book configuration, but you can force a specific version using --gitbook option:
```bash
$ gitbook build ./mybook --gitbook=2.0.1
```
and list available commands in this version using:
```bash
$ gitbook help --gitbook=2.0.1
```
### Manage versions
List installed versions:
```bash
$ gitbook versions
```
List available versions:
```
$ gitbook versions:available
```
Install a specific version:
```
$ gitbook versions:install 2.1.0
```
Uninstall a specific version
```
$ gitbook versions:uninstall 2.0.1
```
Use a local folder as a GitBook version (for developement)
```
$ gitbook versions:link 2.0.1-alpha ./mygitbook
```
