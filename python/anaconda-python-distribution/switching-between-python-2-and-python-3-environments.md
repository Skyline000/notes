# Switching between Python 2 and Python 3 environments

## Step 1:安裝及更新conda <a id="5361"></a>

安裝部分可參考筆者[**Anaconda介紹及安裝教學**](https://medium.com/@chihlo/anaconda%E4%BB%8B%E7%B4%B9%E5%8F%8A%E5%AE%89%E8%A3%9D%E6%95%99%E5%AD%B8-f7dae6454ab6)或[**官方說明**](https://docs.anaconda.com/anaconda/install/)，同時確認作業系統及你所需的python版本。在Windows開始選單\(Start menu\)中選擇Anaconda Prompt\(如下圖所示\)：![](https://miro.medium.com/max/306/0*0LdsxVFfRMfiGW-2.png)

此時可以輸入下列命令來檢查目前版本。

```text
conda –V
```

{% hint style="warning" %}
Below error may occur "LookupError: unknown encoding: 65001"

Enter "set pythonioencoding=utf-8" to set the environment variable first
{% endhint %}

![](../../.gitbook/assets/image%20%2851%29.png)

{% hint style="info" %}
Long-term solution

Unclick the "Use Unicode UTF-8 for worldwide language support" setting.
{% endhint %}

![](../../.gitbook/assets/image%20%2875%29.png)

## Step 2:建立虛擬環境 <a id="76f3"></a>

你可以輸入下面命令看目前系統已經安裝幾個虛擬環境。

```text
conda env list
```

![](../../.gitbook/assets/image%20%2825%29.png)

假設我們要建立一個叫做py3的虛擬環境，並且是安裝python 3.7的版本，那我們可以鍵入下面的命令。

```text
conda create --name py3 python=3.7
```

安裝完後會出現如下圖所示，提醒啟動與關閉虛擬環境的用法。

![](../../.gitbook/assets/image%20%2887%29.png)

你可以進入Anaconda Navigator看到你目前環境及所對應的安裝項目，與Anaconda Prompt底下所看到的是一樣的。

![](../../.gitbook/assets/image%20%2896%29.png)

如果要在此虛擬環境下安裝所需套件，例如numpy那只需要輸入下令命令即可。

```text
conda install numpy
```

## Steps 3: Switching between Python 2 and Python 3

Now we can launch different version Python and Spyder.

![](../../.gitbook/assets/image%20%2863%29.png)

## Reference

{% embed url="https://medium.com/python4u/%E7%94%A8conda%E5%BB%BA%E7%AB%8B%E5%8F%8A%E7%AE%A1%E7%90%86python%E8%99%9B%E6%93%AC%E7%92%B0%E5%A2%83-b61fd2a76566" %}

{% embed url="https://docs.anaconda.com/anaconda/user-guide/tasks/switch-environment/" %}

{% embed url="https://www.jianshu.com/p/dba708360b9d" %}



