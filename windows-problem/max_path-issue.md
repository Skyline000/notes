# MAX\_PATH issue

> In the Windows API \(with some exceptions discussed in the following paragraphs\), the maximum length for a path is **MAX\_PATH**, which is defined as 260 characters. A local path is structured in the following order: drive letter, colon, backslash, name components separated by backslashes, and a terminating null character. For example, the maximum path on drive D is "D:\_some 256-character path string_" where "" represents the invisible terminating null character for the current system codepage. \(The characters &lt; &gt; are used here for visual clarity and cannot be part of a valid path string.\)
>
> [https://docs.microsoft.com/en-us/windows/desktop/FileIO/naming-a-file](https://docs.microsoft.com/en-us/windows/desktop/FileIO/naming-a-file)



## Solution

 `Computer Configuration` -&gt; `Admin Templates` -&gt; `System` -&gt; `FileSystem`

![](../.gitbook/assets/image%20%2842%29.png)

![](../.gitbook/assets/image%20%2846%29.png)

Reference: [https://stackoverflow.com/questions/27680647/does-max-path-issue-still-exists-in-windows-10](https://stackoverflow.com/questions/27680647/does-max-path-issue-still-exists-in-windows-10)

