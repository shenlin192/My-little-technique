# Ubuntu 4.01.0 遇到的问题

##解决Ubuntu中无法连接wifi的方法
`sudo bash`    
`echo "options rtl8723be fwlps=0 swlps=0" > /etc/modprobe.d/rtl8723be.conf `   
`reboot`   

##彻底删除 ocaml
` sudo apt-get remove  ocaml-base-nox`

##反色

windows: 放大器 win+"+" 反色: contrl+alt+I
ubuntu pdf: contrl+I  
chrome 有dark theme  
firefox 也是  
