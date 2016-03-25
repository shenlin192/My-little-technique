#解决Ubuntu中无法连接wifi的方法
'sudo bash
echo "options rtl8723be fwlps=0 swlps=0" > /etc/modprobe.d/rtl8723be.conf
reboot' 