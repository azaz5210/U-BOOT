# U-BOOT
B0822003陳弘昇、B0942003 賴柏楷、B0942209 吳崧瑋

開始前請將你的ubuntu給至少35g空間，不然你會後悔

全稱Universal Boot Loader,是遵循GPL條款的開源程式碼項目

這次是以QEMU搭建linux+u-boot

# QEMU簡介

QEMU是一個模擬器，可以模擬CPU，ARM、X86、MIPS等架構

可以模擬的ARM處理器：ARM926E、ARM1136、Cortex-A8/A9

模擬真實的開發板、外設：串列埠、LCD、網絡卡、USB、SD卡…

# 使用QEMU的事情

研究核心虛擬化

模擬CPU，對於晶片公司，流片之前在QEMU上做驗證、模擬、軟硬體協同設計，開發BSP和驅動

模擬開發板，在模擬平臺上進行系統軟體開發、驅動開發

學生、工程師可以利用qemu-system-arm學習嵌入式開發、研究Bootloader 、Linux核心、驅動開發、應用開發等。

# QEMU學習嵌入式的好處

節省學習成本

跳過開發板、硬體的各種“坑”，縮短學習曲線

重構嵌入式知識體系和技能，跟硬體無關的放到QEMU上學習

跟開發板相關的驅動、BSP針對具體開發板深入突破

適應不同CPU、開發板的技術要求

# 正片開始

## 1.renew file

sudo apt-get update

## 2.install u-boot tools

sudo apt-get install u-boot-tools

## 3.切換權限至root(若不想切也沒差，只是在指令方面都要用sudo)


![image](https://user-images.githubusercontent.com/90091174/173046734-96dc8ac6-73d6-437e-a3dc-e1a2dc0bcd58.png)


## 4.安裝:交叉編譯器

交叉編譯

在一種計算機環境中編譯程式，在另外一種環境下執行。

或者說在一個平臺上編譯生成在另一個平臺上執行的可執行程式碼。


指令: apt-get install gcc-arm-linux-gnueabi   ##若此無法下載請先google找如何安裝gcc

檢查版本指令:  arm-linux-gnueabi-gcc -v


![image](https://user-images.githubusercontent.com/90091174/173049683-bb642d62-b7cd-4fcd-8160-1f5ba809538b.png)


## 5.安裝qemu(使用qemu安裝虛擬機)

指令:  sudo apt-get install qemu

## 6.安裝包

![image](https://user-images.githubusercontent.com/90091174/173517966-ffe7c1ba-e32a-4dc0-85b7-2922eea87507.png)


指令:wget http://wiki.qemu-project.org/download/qemu-2.0.0.tar.bz2

指令:tar xjvf qemu-2.0.0.tar.bz2

GIT:git clone git://git.qemu-project.org/qemu.git
 
## 7.安裝Python(版本1)
sudo apt-get install python

## 8.指令:cd qemu-2.0.0

指令:./configure --target-list=arm-softmmu --audio-drv-list=

發生錯誤  解決方案 : sudo apt-get install gcc

![image](https://user-images.githubusercontent.com/90091174/173519614-16001df3-d769-467c-b5a6-6bf1fe83361f.png)

![image](https://user-images.githubusercontent.com/90091174/173523866-d8d8671a-0fbe-4293-a67e-8398f79e9261.png)

## 9.指令:sudo apt install make

## 10.QEMU支援的開發版:qemu-system-arm -M help //列出支援的開發板(執行此碼會發生錯誤，請自行修正)

![image](https://user-images.githubusercontent.com/90091174/173522755-156a0b7a-3fb1-4fa7-a883-85b7ff92b422.png)


## 11.下載linux核心與dtb檔案
指令:git clone git://git.kernel.org/pub/scm/linux/kernel/git/stable/linux-stable.git/

或者去linux官網(建議) www.kernel.org

![image](https://user-images.githubusercontent.com/90091174/173365969-de988204-b55c-40c4-a777-041ef93b27c6.png)

### 修改核心根目錄的Makefile

![image](https://user-images.githubusercontent.com/90091174/173366274-97681579-f954-433b-876f-e037cbed7ebb.png)

### 找到這兩行

![image](https://user-images.githubusercontent.com/90091174/173367273-0940c9d5-c612-4e76-957b-38069d5ba57a.png)

### 更改成

![image](https://user-images.githubusercontent.com/90091174/173367652-3606478b-eb83-4173-9b0a-cf7b712b51e9.png)

## 12.將載好linux解壓縮至桌面，這樣方便使用cd呼叫檔案

## 13.練習確認檔案位置

![image](https://user-images.githubusercontent.com/90091174/173391614-90559e2d-06bf-4729-9364-f0f979a3c926.png)

## 14.使用cd進入至linux檔案中 ##指令ls是查看該路徑下檔案

![image](https://user-images.githubusercontent.com/90091174/173396704-2cb2c859-f1f8-4a3d-a341-91a55a4e5fa9.png)

## 15.編譯核心、模組、dtb檔案

![image](https://user-images.githubusercontent.com/90091174/173397544-146211b3-3370-4ce8-8f41-72a53c01b862.png)

## 有錯誤再用下圖指令

![image](https://user-images.githubusercontent.com/90091174/173530559-acc260d5-7af8-4820-9b23-2eebae952418.png)

## 成功後

![image](https://user-images.githubusercontent.com/90091174/173530927-1517c0a4-e7af-4a6a-8d50-b355e064b3b8.png)

![image](https://user-images.githubusercontent.com/90091174/173531616-a7bd5985-3a22-4015-bea6-cec86005b26c.png)

![image](https://user-images.githubusercontent.com/90091174/173531694-17e55f6b-e4dd-4a80-aa66-e3434a6c68c9.png)


# 執行核心

指令: qemu-system-arm -M vexpress-a9 -m 512M -kernel arch/arm/boot/zImage -dtb arch/arm/boot/dts/vexpress-v2p-ca9.dtb -nographic -append “console=ttyAMA0”

![image](https://user-images.githubusercontent.com/90091174/173548582-8728278a-b3e0-4b11-a787-7229dbf60fcb.png)

## 關閉qemu
ps -a檢視程序號

kill -9 pid 關閉程序

![image](https://user-images.githubusercontent.com/90091174/173548864-5f107f41-224c-497c-8abf-289629d91caa.png)

# BusyBOX
一個整合100多個Linux常用命令和工具的軟體

一個適合製作嵌入式檔案系統的軟體工具

## 編譯安裝

![image](https://user-images.githubusercontent.com/90091174/174972738-88b838dd-1e60-427b-950c-6681aa55eef4.png)

遇到問題

![image](https://user-images.githubusercontent.com/90091174/174972873-6293bba9-bf3d-4eaa-8866-e7d26f8844fc.png)

解決辦法

您可以直接編輯源列表 ( /etc/apt/sources.list)。我認為您需要添加/取消註釋這些行：

deb-src http://archive.ubuntu.com/ubuntu trusty main restricted #Added by software-properties
deb-src http://gb.archive.ubuntu.com/ubuntu/ trusty restricted main universe multiverse #Added by software-properties
deb-src http://gb.archive.ubuntu.com/ubuntu/ trusty-updates restricted main universe multiverse #Added by software-properties
deb-src http://gb.archive.ubuntu.com/ubuntu/ trusty-backports main restricted universe multiverse #Added by software-properties
deb-src http://security.ubuntu.com/ubuntu trusty-security restricted main universe multiverse #Added by software-properties
deb-src http://gb.archive.ubuntu.com/ubuntu/ trusty-proposed restricted main universe multiverse #Added by software-properties

![image](https://user-images.githubusercontent.com/90091174/174977809-b9d46f79-546b-47dc-ae67-aa4f8c3675d5.png)



# 參考資料:

https://cloud.tencent.com/developer/article/1018022?from=15425

https://www.gushiciku.cn/pl/pTch/zh-tw



