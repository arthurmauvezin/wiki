# Documentation project 

The goal of this documentation is to stop stack overflow syndrom (going to same page every time I search for something, and re-reading full page) and capitalize on all stuff I learn here instead.
This documentation is available at: https://wiki.autopdutop.fr

## Usage

[Official installation Guide](http://www.mkdocs.org/)

### Prerequisites
* Python installed
* Pip installed

### Get project
```bash
git clone https://github.com/arthurmauvezin/wiki.git
```

### Install Mkdocs and themes
```bash
pip install --user mkdocs mkdocs-material pygments
```

### Add command to path
```bash
sudo cp install/mkdocs /usr/local/bin
sudo chmod 755 /usr/local/bin/mkdocs
```

### Start server
```bash
cd wiki
mkdocs serve
```

### Build site
```bash
mkdocs build
```

### Useful Aliases (add to .bashrc or .zshrc)
```bash
#### WIKI ####
alias wiki-start='cd ~/wiki/ && nohup mkdocs serve &>/dev/null &'
alias wiki-stop='kill -9 $(pgrep -a mkdocs | cut -d '"'"' '"'"' -f 1)'
alias wiki-reload='wiki-stop && wiki-start'
alias wiki='if ! [[ $(pgrep -a mkdocs) ]]; then wiki-start; fi && google-chrome-stable --app=http://localhost:8000'
```
