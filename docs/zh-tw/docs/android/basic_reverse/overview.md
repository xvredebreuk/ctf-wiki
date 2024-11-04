# Android 逆向基本介紹

首先，我們需要明確一下 Android 逆向的目的： **希望分析出程序的功能** 。那麼我們自然也就有兩個方面（方法與對象）可以考慮

- 分析方法，可以採用以下方式
    - 靜態分析，對源代碼進行逆向，然後閱讀分析
    - 動態分析，對代碼進行動態調試，一般來說動態分析離不開靜態分析。
- 分析對象，一般有以下兩類對象
    - java，層代碼
    - 原生層代碼

不難看出，要想分析 Android 應用，基本的 java 層的知識與原生層的知識還是有必要掌握的。

目前來說，Android 逆向主要應用於以下幾個方向

1. app 安全審查
2. 系統漏洞挖掘
3. 惡意代碼殺查
4. 同行業產品技術原理分析
5. 移除安全機制