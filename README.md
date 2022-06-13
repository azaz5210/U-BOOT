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

5.安裝qemu(使用qemu安裝虛擬機)
指令: sudo apt-get install qemu

6.安裝包
指令:wget http://wiki.qemu-project.org/download/qemu-2.0.0.tar.bz2
    :tar xjvf qemu-2.0.0.tar.bz2
 GIT:git clone git://git.qemu-project.org/qemu.git
 
 7.安裝Python(版本1)
   sudo apt-get install python

8.指令:cd qemu-2.0.0
     :./configure --target-list=arm-softmmu --audio-drv-list=

![image](https://user-images.githubusercontent.com/90091174/173354531-367d5024-5ef3-431c-a5e4-83220647a76b.png)

9.指令:sudo make install(約下載10分鐘)
10.QEMU支援的開發版:qemu-system-arm -M help //列出支援的開發板

![image](https://user-images.githubusercontent.com/90091174/173358916-1e3e4010-873e-4036-9f7d-4f7caa15a631.png)

11.下載linux核心與dtb檔案
指令:git clone git://git.kernel.org/pub/scm/linux/kernel/git/stable/linux-stable.git/

![image](https://user-images.githubusercontent.com/90091174/173304836-62110a40-d60a-40e1-b211-7e636a70c1f9.png)

7.
