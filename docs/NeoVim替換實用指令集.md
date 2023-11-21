# Neovim Editor 文字替換使用實例

## 摘要

在 YAML 設定檔，本有內容如下：

```
  - xform/;n(?!g)/〖柳;/
  - xform/;ng/〖語;/
  - xform/;m/〖文;/
  - xform/;ts(?!h)/〖曾;/
  - xform/;tsh/〖出;/
```

現在想要將每一行中的「第二個斜線」至「行尾」的內容去除。

【舉例】： `- xform/;tsh/〖出;/`

每一行的行內共有 3 個「斜線」字元；自第 2 個斜線之後的
第一個字元到「行尾」 的內容欲去除，即： `〖出;/` 需去除。

所以：`- xform/;tsh/〖出;/` ，只留： `- xform/;tsh/`  。

## 需求解析

在 Neovim Editor ，可使用「替換」指令（Search and Replace），
將第二個斜線之後至行尾的字元清除。

【替換執行前】： - xform/;tsh/〖出;/

【替換執行後】： - xform/;tsh/

## 解決方案

為滿足以上之需求，需以「正規表達式」（Regular Expression），
來進行「替換」（Search and Replace）。

替換指令之內容如下：

```
:%s/\(\/[^\/]*\)\/.*/\1/\/g
```

## 練習

```
    - xform/;n(?!g)/〖柳;/
    - xform/;ng/〖語;/
    - xform/;m/〖文;/
    - xform/;ts(?!h)/〖曾;/
    - xform/;tsh/〖出;/
    #======================================
    - xform/;l/〖柳;/
    - xform/;p(?!h)/〖邊;/
    - xform/;k(?!h)/〖求;/
    - xform/;kh/〖去;/
    - xform/;t(?!h)/〖地;/
    - xform/;ph/〖頗;/
    - xform/;th/〖他;/
    # - xform/;c(?!h)/〖曾;/
    - xform/;j/〖入;/
    - xform/;s/〖時;/
    # - xform/;q/〖英;/
    - xform/;ø/〖英;/
    - xform/;b/〖文;/
    - xform/;g/〖語;/
    # - xform/;ch/〖出;/
    - xform/;h/〖喜;/
    #------------------------------------------------------
    - xform/;u(n|t)(\d)/君;$2/
    - xform/;ia(n|t)(\d)/堅;$2/
    - xform/;i(m|p)/金;/
    - xform/;ui(h?)(\d)/規;$2/
    - xform/;ee(h?)/嘉;/
    - xform/;a(n|t)(\d)/干;$2/
    - xform/;o(ng|k)/公;/
    - xform/;uai(h?)/乖;$2/
    - xform/;e(ng|k)/經;/
    - xform/;i(ng|k)/經;/
    - xform/;ua(n|t)(\d)/觀;$2/
    # - xform/;ou(h?)(\d)/沽;$2/
    - xform/;iau(h?)(\d)/嬌;$2/
    - xform/;ei/稽;/
    - xform/;io(ng|k)/恭;/
    # - xform/;o(h?)(\d)/高;$2/
    - xform/;ai(\d)/皆;$1/
    - xform/;i(n|t)(\d)/巾;$2/
    - xform/;ia(ng|k)/姜;/
    - xform/;a(m|p)/甘;/
    - xform/;ua(h?)(\d)/瓜;$2/
    - xform/;a(ng|k)/江;/
    - xform/;ia(m|p)/兼;/
    - xform/;au(h?)(\d)/交;$2/
    - xform/;ia(h?)(\d)/迦;$2/
    - xform/;ue(h?)(\d)/檜;$2/
    - xform/;ann(h?)/監;/
    - xform/;u(h?)(\d)/艍;$2/
    - xform/;a(h?)(\d)/膠;$2/
    - xform/;i(h?)(\d)/居;$2/
    - xform/;iu(\d)/丩;$1/
    - xform/;enn(h?)/更;/
    - xform/;inn(h?)/梔;/
    - xform/;iann/驚;/
    - xform/;uann/官;/
    - xform/;e(h?)(\d)/伽;$2/
    - xform/;ainn(h?)/閒;/
    # - xform/;ounn/姑;/
    - xform/;uenn/糜;/
    - xform/;iaunn(h?)/嘄;/
    - xform/;o(m|p)/箴;/
    - xform/;aunn/爻;/
    # - xform/;onn(h?)/扛;/
    - xform/;iunn/牛;/
    #======================================
    - xform/;io/茄;/
    - xform/;ng/鋼;/
    - xform/;oo(h?)(\d)/沽;$2/
    - xform/;o(h?)(\d)/高;$2/
    # - xform/;oonn/姑;/
    - xform/;ounn/姑;/
    - xform/;onn(h?)/扛;/
```
