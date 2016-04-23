## Tmux + Wemux Cheat Sheet

### Servers  
`wemux foo` to launch a server session  
`chmod 1777 /tmp/wemux-host`you might have to fix permissions  
`wemux join foo` to join a server and then `wemux attach` or just `wemux`  
`C-b d` to detach from the server  

### Windows*
*windows are kind of like desktops in GUI world  
  
`C-b c` create new window  
`C-b ,` rename window  
`C-b n` move to the next window  
`C-b p` move to the previous window  
`C-b l` move to the previously selected window  

### Panes*
*panes are kind of like windows in GUI world  
  
`C-b -` split the pane vertically  
`C-b \` split the pane horizontally  
`C-b o` go to next pane  
`C-b q` show pane numbers 
`C-b {` move the current pane left  
`C-b }` move the current pane right  
`C-b x` kill pane  
`C-b [` history + vi browsing mode  
`C-b space` toggle between layouts  
