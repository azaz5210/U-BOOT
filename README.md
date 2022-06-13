# U-BOOT
B0822003陳弘昇、B0942003 賴柏楷、B0942209 吳崧瑋

全稱Universal Boot Loader,是遵循GPL條款的開源程式碼項目

這次是以

1.renew file: sudo apt-get update

![image](https://user-images.githubusercontent.com/90091174/173024997-d05fa358-7852-4b65-a89f-d3b9dc7274cf.png)

2.install u-boot tools

![image](https://user-images.githubusercontent.com/90091174/173028194-03231ffc-bc79-400d-8de3-665f958ee979.png)

3.切換權限至root

![image](https://user-images.githubusercontent.com/90091174/173046734-96dc8ac6-73d6-437e-a3dc-e1a2dc0bcd58.png)

![image](https://user-images.githubusercontent.com/90091174/173050283-011fbf76-80f8-404e-9dad-c434fc5e2ce1.png)

4.安裝:交叉編譯器
指令:apt-get install gcc-arm-linux-gnueabi   ##若此無法下載請先google找如何安裝gcc

檢查版本指令:arm-linux-gnueabi-gcc -v

![image](https://user-images.githubusercontent.com/90091174/173049683-bb642d62-b7cd-4fcd-8160-1f5ba809538b.png)

5.安裝qemu
指令: sudo apt-get install qemu

6.下載linux核心與dtb檔案

![image](https://user-images.githubusercontent.com/90091174/173304836-62110a40-d60a-40e1-b211-7e636a70c1f9.png)

7.
