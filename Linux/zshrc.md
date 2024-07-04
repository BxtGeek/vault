```
alias ssm="sshmenu"
alias ipaddr="ifconfig en0 | grep -w inet | cut -d' ' -f2"
eval "$(atuin init zsh)"
alias speed="speedtest-cli --simple" 
alias wtr="curl wttr.in"
neofetch
PS1='[%*]-[%j]-[%m] %~ '
```
