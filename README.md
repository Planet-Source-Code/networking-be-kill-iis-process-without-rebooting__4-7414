<div align="center">

## Kill IIS process without rebooting


</div>

### Description

Ever had to restart IIS when it was caught up in a loop, or doing some other stuff which results in IIS not coming down. Service manager fails to stop the www service, task manager gets the "Permission denied error". Only way out is a reboot? Not true!
 
### More Info
 


<span>             |<span>
---                |---
**Submitted On**   |
**By**             |[Networking\.be](https://github.com/Planet-Source-Code/PSCIndex/blob/master/ByAuthor/networking-be.md)
**Level**          |Beginner
**User Rating**    |4.8 (72 globes from 15 users)
**Compatibility**  |ASP \(Active Server Pages\)
**Category**       |[System Services/ Functions](https://github.com/Planet-Source-Code/PSCIndex/blob/master/ByCategory/system-services-functions__4-23.md)
**World**          |[ASP / VbScript](https://github.com/Planet-Source-Code/PSCIndex/blob/master/ByWorld/asp-vbscript.md)
**Archive File**   |[](https://github.com/Planet-Source-Code/networking-be-kill-iis-process-without-rebooting__4-7414/archive/master.zip)





### Source Code

<P><BR><B>Killing IIS</B><P>
<FONT SIZE=-2>
We've probably all been in an endless-loop situation, or in a situation where your dll called from ASP hangs (every used a msgbox in a dll?).
<p>Bottom line, we need to restart the IIS services. However, because the process is still active, the service manager isn't able to shut it down. When trying to forcefully kill the inetinfo.exe process, or the DLLHOST.EXE process your dll is running in, we get a permission denied error, even when doing this as an administrator. In this case, you probably ended up rebooting the machine...
<p>However, you don't need to. There's a tool from Microsoft, which is installed when installing IIS. It is called iisreset, and can be found in the winnt\system32 folder. This can be run from the command line, and takes a few parameters. The most important are:
<P>
<TABLE BORDER=1>
<TR><TD>/RESTART</TD><TD>Stops and starts IIS</TD></TR>
<TR><TD>/START</TD><TD>Starts IIS (if stopped)</TD></TR>
<TR><TD>/STOP</TD><TD>Stops IIS (if started)</TD></TR><TR><TD>/REBOOT</TD><TD>Reboots the PC</TD></TR>
<TR><TD>/REBOOTONERROR</TD><TD>Reboots the PC if it fails to stop IIS without forcing it</TD></TR>
<TR><TD>/NOFORCE</TD><TD>Do not force it to stop</TD></TR>
<TR><TD>/TIMEOUT:X</TD><TD>After X seconds, IIS is forced to stop, unless /NOFORCE was given. If /REBOOTONERROR was given, this will reboot the system.</TD></TR>
</TABLE>
<P>
This can save you a lot of time, since you don't have to reboot the entire system. Very usefull in systems that have a high load, since downtimes are shorter.
<P>I hope this is of use for anyone, it was (and I'm sure it will always be) for me.

