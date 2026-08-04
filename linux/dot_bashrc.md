```
alias ll='ls -alF'
alias la='ls -A'
alias l='ls -CF'
alias lsblkbat='lsblk | bat -l conf -p'

alias nv='nvim'
alias vi='nvim'
alias vim='nvim'

alias t='tmux'
alias ta='tmux attach'
alias tl='tmux ls'

alias cpwd="pwd | xclip -selection clipboard"
```

### ===== NAVIGATION =====
```
alias ..='cd ..'
alias ...='cd ../..'
alias ....='cd ../../..'
alias ~='cd ~'
alias -- -='cd -'
```

### ===== LS =====
```
alias ls='ls --color=auto'
alias ll='ls -lah'
alias la='ls -A'
alias l='ls -CF'
```

### ===== SAFETY =====
```
alias crontab='crontab -i'
alias sudo='sudo '
#alias rm='rm -i' always useful but uncomment it at least on prod server!
#alias mv='mv -i'
```

### ===== GREP =====
```
alias grep='grep --color=auto'
alias egrep='egrep --color=auto'
alias fgrep='fgrep --color=auto'
```

### ===== DISK & MEMORY =====
```
alias df='df -h'
alias du='du -h'
alias free='free -h'
alias disk='df -h | grep -v tmpfs'
```

### ===== NETWORKING =====
```
alias ports='netstat -tulpn'
alias myip='curl -s ifconfig.me'
alias ping='ping -c 5'
```

### ===== PROCESS =====
```
alias psg='ps aux | grep -v grep | grep'
alias top10='ps aux --sort=-%mem | head -11'
```

### ===== SYSTEM =====
```
alias update='apk update && apk upgrade'
alias installed='apk info'
alias search='apk search'
```

### ===== FILES =====
```
alias h='history'
alias c='clear'
alias path='echo $PATH | tr : "\n"'
alias now='date +"%Y-%m-%d %H:%M:%S"'
alias sizeof='du -sh'
```

### ===== DOCKER =====
```
alias d='docker'
alias dc='docker compose'
alias dps='docker ps'
alias dpsa='docker ps -a'
alias di='docker images'
alias dex='docker exec -it'
alias dlogs='docker logs -f'
alias dstop='docker stop $(docker ps -q)'
alias dprune='docker system prune -af'
alias dvol='docker volume ls'
alias dnet='docker network ls'
```

### ===== DOCKER COMPOSE =====
```
alias dcup='docker compose up -d'
alias dcdown='docker compose down'
alias dcrestart='docker compose restart'
alias dclogs='docker compose logs -f'
alias dcbuild='docker compose build --no-cache'
alias dcps='docker compose ps'
```

### ===== PYTHON =====
```
alias py='python3'
alias pip='pip3'
alias venv='python3 -m venv venv'
alias activate='source venv/bin/activate'
alias pipreq='pip freeze > requirements.txt'
alias pipinstall='pip install -r requirements.txt'
alias pyserve='python3 -m http.server'
```

### ===== GIT =====
```
alias g='git'
alias gs='git status'
alias ga='git add'
alias gaa='git add .'
alias gc='git commit -m'
alias gp='git push'
alias gl='git pull'
alias glog='git log --oneline -10'
alias gd='git diff'
alias gb='git branch'
alias gco='git checkout'
```

### ===== QUICK EDITS =====
```
alias profile='vi ~/.profile'
alias reload='source ~/.profile'
```

### ===== MISC =====
```
alias weather='curl wttr.in/?0'
alias cheat='curl cheat.sh/'
```

### Create dir and cd into it
```
mkcd() { mkdir -p "$1" && cd "$1"; }
```

### Quick find
```
f() { find . -name "*$1*"; }
```

### Docker shell into container
```
dsh() { docker exec -it $1 /bin/sh; }
```
