# Set a automatic ping test in Windows when startup

## Prepare a batch file for ping script

{% hint style="warning" %}
Do not use reserved / special words to name the batch files, e.g. ping.bat.
{% endhint %}

{% code-tabs %}
{% code-tabs-item title="pingtest.bat" %}
```bash
@echo off
for /f "delims=" %%a in ('wmic OS Get localdatetime  ^| find "."') do set dt=%%a
set dt=%dt:~0,8%%
ping -t 127.0.0.1|cmd /q /v /c "(pause&pause)>nul & for /l %%a in () do (set /p "data=" && echo(!date! !time! !data!)&ping -n 2 127.0.0.1>nul" >> C:\pingresult\result_%dt%.txt
```
{% endcode-tabs-item %}
{% endcode-tabs %}

[`@echo off`](https://docs.microsoft.com/en-us/windows-server/administration/windows-commands/echo) turns off the command echoing feature.

Save the result to `C:\pingresult\result_%dt%.txt` with date in filename.

#### Sample output

{% code-tabs %}
{% code-tabs-item title="result\_20190928.txt" %}
```text
28/09/2019 22:09:48.45 Pinging 127.0.0.1 with 32 bytes of data:
28/09/2019 22:09:49.46 Reply from 127.0.0.1: bytes=32 time<1ms TTL=128
28/09/2019 22:09:50.48 Reply from 127.0.0.1: bytes=32 time<1ms TTL=128
28/09/2019 22:09:51.49 Reply from 127.0.0.1: bytes=32 time<1ms TTL=128
28/09/2019 22:09:52.50 Reply from 127.0.0.1: bytes=32 time<1ms TTL=128
```
{% endcode-tabs-item %}
{% endcode-tabs %}

## Create a EXE to execute 

{% hint style="info" %}
Only run batch file also work fine, but the cmd can't be hidden. If want to run it as a background job, then create a EXE and put in startup folder to run at PC startup.
{% endhint %}

Type "iexpress" and open it.

{% hint style="info" %}
Better run as administrator
{% endhint %}

![](../../.gitbook/assets/image%20%2835%29.png)



![](../../.gitbook/assets/image%20%2861%29.png)



![](../../.gitbook/assets/image%20%2876%29.png)



![](../../.gitbook/assets/image%20%2816%29.png)



![](../../.gitbook/assets/image%20%2877%29.png)



![](../../.gitbook/assets/image%20%2837%29.png)

Add the batch file that prepare before.

![](../../.gitbook/assets/image%20%2811%29.png)

Enter the command want to execute, e.g. `cmd /c C:\pingresult\pingtest.bat`

{% hint style="info" %}
Maybe better to specific the path
{% endhint %}

![](../../.gitbook/assets/image%20%2895%29.png)

Select "Hidden" to hidden the cmd window.

![](../../.gitbook/assets/image%20%2889%29.png)



![](../../.gitbook/assets/image%20%2882%29.png)

Enter the path want to save the EXE.

![](../../.gitbook/assets/image%20%2845%29.png)



![](../../.gitbook/assets/image%20%2897%29.png)



![](../../.gitbook/assets/image%20%2860%29.png)



![](../../.gitbook/assets/image%20%2843%29.png)



![](../../.gitbook/assets/image.png)

{% hint style="warning" %}
If below error occur, please run this wizard as administrator.
{% endhint %}

![](../../.gitbook/assets/image%20%2846%29.png)

## Put the EXE in Startup folder.

1. Press **Start**, type **Run**, and press Enter.
2. In the Run window, type **shell:startup** to open the Startup folder.
3. Once the Startup folder is opened, paste the EXE file into the Startup folder.

```text
C:\Users\Username\AppData\Roaming\Microsoft\Windows\Start Menu\Programs\Startup
```

![](../../.gitbook/assets/image%20%2848%29.png)

![](../../.gitbook/assets/image%20%2820%29.png)



## Reference

{% embed url="https://www.youtube.com/watch?v=5ADyETHPChk" %}

{% embed url="https://www.scribd.com/document/234458681/IExpress-Windows-7-Error-Creating-Process-Fix-Supportive-Technical-Bloggings" %}

{% embed url="https://superuser.com/questions/1205359/iexpress-error-unable-to-open-makecab-file" %}

{% embed url="https://www.computerhope.com/issues/ch000322.htm" %}

{% embed url="https://www.thewindowsclub.com/startup-folder-in-windows-8" %}





