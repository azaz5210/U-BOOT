# U-BOOT
B0822003陳弘昇、B0942003 賴柏楷、B0942209 吳崧瑋

開始前請將你的ubuntu給至少35g空間，不然你會後悔

全稱Universal Boot Loader,是遵循GPL條款的開源程式碼項目

這次是以QEMU搭建linux+u-boot

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

或者去linux官網(建議) www.kernel.org

![image](https://user-images.githubusercontent.com/90091174/173365969-de988204-b55c-40c4-a777-041ef93b27c6.png)

修改核心根目錄的Makefile

![image](https://user-images.githubusercontent.com/90091174/173366274-97681579-f954-433b-876f-e037cbed7ebb.png)

找到這兩行

![image](https://user-images.githubusercontent.com/90091174/173367273-0940c9d5-c612-4e76-957b-38069d5ba57a.png)

更改成

![image](https://user-images.githubusercontent.com/90091174/173367652-3606478b-eb83-4173-9b0a-cf7b712b51e9.png)

12.將載好linux解壓縮至桌面，這樣方便使用cd呼叫檔案

13.練習確認檔案位至

![image](https://user-images.githubusercontent.com/90091174/173391614-90559e2d-06bf-4729-9364-f0f979a3c926.png)

14.使用cd進入至linux檔案中 ##指令ls是查看該路徑下檔案

![image](https://user-images.githubusercontent.com/90091174/173396704-2cb2c859-f1f8-4a3d-a341-91a55a4e5fa9.png)

15.編譯核心、模組、dtb檔案
先安裝東西sudo apt-get install flex 在打下面圖片指令 ##對，我很懶 第二個指令可以跳過  他的檔案他媽的有夠大，會讓你重灌

![image](https://user-images.githubusercontent.com/90091174/173397544-146211b3-3370-4ce8-8f41-72a53c01b862.png)

