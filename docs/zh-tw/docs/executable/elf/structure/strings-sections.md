# String Sections

## .strtab: String Table

該節區描述默認的字符串表，包含了一系列的以 NULL 結尾的字符串。ELF 文件使用這些字符串來存儲程序中的符號名，包括

-   變量名
-   函數名

該節在運行的過程中不需要加載，只需要加載對應的子集 .dynstr 節。

一般通過對字符串的首個字母在字符串表中的下標來索引字符串。

字符串表的首尾字節都是NULL。此外，索引爲 0 的字符串要麼沒有名字，要麼就是名字爲空，其解釋依賴於上下文。字符串表也可以爲空，相應的，其節區頭部的 sh_size 成員將爲 0。在空字符串表中索引大於 0 的下標顯然是非法的。

一個節區頭部的 sh_name 成員的值爲其相應的節區頭部字符串表節區的索引，此節區由 ELF 頭的 e_shstrndx 成員給出。下圖給出了一個包含 25 個字節的字符串表，以及與不同索引相關的字符串。

| 索引 | +0   | +1   | +2   | +3   | +4   | +5   | +6   | +7   | +8   | +9   |
| ---- | ---- | ---- | ---- | ---- | ---- | ---- | ---- | ---- | ---- | ---- |
| 0    | \0   | n    | a    | m    | e    | .    | \0   | V    | a    | r    |
| 10   | i    | a    | b    | l    | e    | \0   | a    | b    | l    | e    |
| 20   | \0   | \0   | x    | x    | \0   |      |      |      |      |      |

其中包含的字符串有

| 索引 | 字符串   |
| ---- | -------- |
| 0    | none     |
| 1    | name.    |
| 7    | Variable |
| 11   | able     |
| 16   | able     |
| 24   | 空字符串 |

可以看出

-   字符串表索引可以引用節區中任意字節。
-   字符串可以出現多次。
-   可以存在對子字符串的引用。
-   同一個字符串可以被引用多次。
-   字符串表中也可以存在未引用的字符串。

這部分信息在進行 `strip` 後就會消失。

## .shstrtab: Section Header String Table

該節區與 `.strtab` 的存儲結構類似，不過該節區存儲的是節區名的字符串。
