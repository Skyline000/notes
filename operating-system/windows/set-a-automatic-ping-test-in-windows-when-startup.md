# Set a automatic ping test in Windows when startup

### Prepare a batch file for ping script

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



### Create a EXE to execute 

{% hint style="info" %}
Only run bat also work fine, but the cmd can't hidden. If want to run it as a background job, do the following steps.
{% endhint %}

1. Type "iexpress" and open it

{% hint style="info" %}
Better run as administrator
{% endhint %}

![](../../.gitbook/assets/image%20%2835%29.png)



![](../../.gitbook/assets/image%20%2860%29.png)



![](../../.gitbook/assets/image%20%2875%29.png)



![](../../.gitbook/assets/image%20%2816%29.png)



![](../../.gitbook/assets/image%20%2876%29.png)



![](../../.gitbook/assets/image%20%2837%29.png)



![](../../.gitbook/assets/image%20%2811%29.png)

Enter the command want to execute `cmd /c C:\pingresult\pingtest.bat`

{% hint style="info" %}
Maybe better to specific the path
{% endhint %}

![](../../.gitbook/assets/image%20%2894%29.png)



![](../../.gitbook/assets/image%20%2888%29.png)



![](../../.gitbook/assets/image%20%2881%29.png)



![](../../.gitbook/assets/image%20%2845%29.png)



![](../../.gitbook/assets/image%20%2896%29.png)



![](../../.gitbook/assets/image%20%2859%29.png)



![](../../.gitbook/assets/image%20%2843%29.png)



![](../../.gitbook/assets/image.png)



If below error occur, please run this wizard as administrator

![](../../.gitbook/assets/image%20%2846%29.png)

### Put the EXE in Startup folder.

1. [Create a shortcut](https://www.computerhope.com/issues/ch000739.htm) to the batch file.
2. Once the shortcut is created, [right-click](https://www.computerhope.com/jargon/r/righclic.htm) the shortcut file and select **Cut**.
3. Press [**Start**](https://www.computerhope.com/jargon/s/start.htm), type **Run**, and press Enter.
4. In the Run window, type **shell:startup** to open the Startup folder.
5. Once the Startup folder is opened, click the **Home** tab at the top of the folder and select **Paste** to [paste](https://www.computerhope.com/jargon/p/paste.htm) the shortcut file into the Startup folder.

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





