AutoFileBAK

# 0.项目概述

## 0.1.项目简介

此应用程序项目使用C#语言开发而成,使用.NET Core 3.1作为开发框架.作用是自动复制接入计算机的存储设备内的文件,并且支持识别受信任的白名单存储设备,在其接入时自动将所有备份到的文件拷贝到该设备内.并且项目也支持FTP协议文件传输,支持将备份到的文件自动上传到远程FTP服务器或手动同步所有文件.并且值得一提的是,上述过程均可静默进行,支持开机自启动,即系统没有任何弹窗/执行提示,使用者无法发觉程序的运行.*已知问题:复制文件可能导致系统读写该磁盘速度变慢,上传操作可能导致网络带宽占用

通俗来讲,这个项目可以在对方不知情的情况下拿到他U盘内的文件,也可以识别你的U盘并且把拷到的文件复制进去.当然,我们更提倡使用此程序备份文件.如果您使用此程序从事非法活动,开发者不会为你承担责任.

## 0.2.项目运行

项目需要.NET Core 3.1运行库.目标平台为Windows.*明确不支持其他系统,因为这些系统无法确定盘符.无需尝试.

## 0.3.开源许可

项目采用AGPL-3.0协议进行开源.详情见LICENSE文件.

# 1.如何使用

程序的使用实例主要包括以bat后缀的脚本文件

## 1.1.解压与安装

解压文件到固定的目录,作为启动目录与文件存储目录.除非只是临时使用,否则不建议直接在压缩包内双击运行.

## 1.2.自启动设置

在一体机或者电脑上打开"启动目录安装"的脚本.如果你确定注册表功能可用也可以尝试另外两个安装选项.区别在于:启动目录安装需要在开机时弹出一至两个黑色的脚本任务框并且闪退后才启动程序,注册表安装则不需要,但是由于部分软件的权限管控,注册表部分可能不起作用.纯Install的选项会优先选择注册表安装,如果遇到权限异常就会尝试启动目录安装.建议自行尝试.安装后就可以自动设置为开机自启动,并且开始监听U盘的连接.

## 1.3.自动拷贝功能

如果程序检测到有U盘插入(不在白名单或黑名单内),就会自动开始静默拷贝里面的文件,然后备份到的文件都会存在程序目录下的Backups文件夹里.具体格式为"xxxx-Image",其中"xxxx"是当前正在读取的U盘序列号.要首次备份后才会生成这些备份文件夹.

## 1.4.白名单与黑名单

### 1.4.1白名单

#### 1.4.1.1白名单的功能

白名单指的是受到程序管理员信任的U盘设备.功能是当白名单内的设备接入时,程序识别到这是白名单内的设备后就会自动将Backups内的文件复制到该U盘内的"/AutoFileBAK/Backups"文件夹内(开发者可更改程序自行设定目录).

#### 1.4.1.2如何将设备添加到白名单

首先运行"退出所有进程"脚本文件,防止程序多重执行或闪退.
而后,运行"白名单模式"脚本文件,待程序执行框内出现"Stick your USB Drive into the computer to write it into whitelist."后,插入需要加入白名单的设备.10秒内程序检测到新的盘符就会获取序列号并添加.出现"xxxx added."(xxxx是U盘序列号)的日志提示后说明添加完成.操作结束后,直接关闭命令窗口并再次启动主进程"AutoFileBAK.exe"

#### 1.4.1.3如何管理白名单设备与移除设备

程序目前不包含这些功能,开发团队也并没有将这两个功能提上日程.不过,可以确定的是在接下来的"AutoFileBAK-GUI"项目中将会包含这些功能.如果您需要管理或移除白名单里的设备,请手动编辑程序目录下的"/Setting/WhiteList.txt"文件.

### 1.4.2黑名单

#### 1.4.2.1黑名单的功能

白名单指的是程序管理员不希望备份或信任的U盘设备.此设备接入后,程序将不进行任何操作.

#### 1.4.2.2如何将设备添加到黑名单

首先运行"退出所有进程"脚本文件,防止程序多重执行或闪退.
而后,运行"黑名单模式"脚本文件,待程序执行框内出现"Stick your USB Drive into the computer to write it into blacklist."后,插入需要加入白名单的设备.10秒内程序检测到新的盘符就会获取序列号并添加.出现"xxxx added."(xxxx是U盘序列号)的日志提示后说明添加完成.操作结束后,直接关闭命令窗口并再次启动主进程"AutoFileBAK.exe"

#### 1.4.2.3如何管理黑名单设备与移除设备

程序目前不包含这些功能,开发团队也并没有将这两个功能提上日程.不过,可以确定的是在接下来的"AutoFileBAK-GUI"项目中将会包含这些功能.如果您需要管理或移除黑名单里的设备,请手动编辑程序目录下的"/Setting/WhiteList.txt"文件.


AutoFileBAK

# 0. Project overview

# 0.1. Project Overview

NET Core 3.1 as the development framework. NET Core 3.1 as the development framework. The purpose of this project is to automatically copy files from the storage device that is connected to the computer, and it supports identifying trusted whitelisted storage devices and automatically copying all backed up files to them when they are connected. And the project also supports FTP protocol file transfer, which supports automatic uploading of the backed up files to a remote FTP server or manual synchronization of all files. And it is worth mentioning that the above process can be carried out silently and supports boot-up, i.e. the system does not have any pop-ups/execution prompts, so the user cannot notice the program running. *Known issues: copying files may cause the system to read and write to the disk slower, upload operations may cause network bandwidth consumption

In layman's terms, this program can get the files on the other party's USB drive without his knowledge, and it can also recognize your USB drive and copy the copied files into it. Of course, we prefer to use this program to backup files. If you use this program for illegal activities, the developer will not be responsible for you.

## 0.2. Running the project

The project requires the .NET Core 3.1 runtime library. The target platform is Windows.* Other systems are explicitly not supported, as they cannot be identified by disk letter. No need to try.

## 0.3. Open Source License

The project uses the AGPL-3.0 protocol for open source . See the LICENSE file for details.

# 1.How to use

Examples of how to use the program include mainly script files with a bat suffix

## 1.1. Decompress and install

Unzip the file into a fixed directory, which will be used as the startup directory and file storage directory. It is not recommended to run the program directly by double-clicking inside the zip file unless it is only for temporary use.

## 1.2. Self-boot settings

Open the "Startup directory installation" script on the all-in-one or PC. If you are sure that the registry function is available, you can also try the other two installation options. The difference is that the boot directory installation requires one or two black script task boxes to pop up and flash before starting the program, while the registry installation does not, but due to some software permissions control, the registry part may not work. If you encounter a permission exception, you will try to start the directory installation. It is recommended to try it by yourself. After installation, it can be set to boot automatically and start listening to the U disk connection.

## 1.3. Automatic copy function

If the program detects a USB flash drive inserted (not in the whitelist or blacklist), it will automatically start to copy the files inside silently, and then the backed up files will be stored in the Backups folder under the program directory. The specific format is "xxxx-Image", where "xxxx" is the serial number of the USB drive being read. These backup folders will be created only after the first backup.

## 1.4. Whitelist and Blacklist

### 1.4.1 Whitelist

#### 1.4.1.1 Function of whitelist

Whitelist refers to the USB devices trusted by the program administrator. The function is that when a whitelisted device is connected, the program will automatically copy the files in Backups to the "/AutoFileBAK/Backups" folder in the USB flash drive after recognizing that it is a whitelisted device (developers can change the program to set the directory).

#### 1.4.1.2 How to add the device to the whitelist

First, run the "Exit all processes" script file to prevent multiple executions or flashbacks.
After that, run the "whitelist mode" script file, wait for the "Stick your USB Drive into the computer to write it into whitelist." to appear in the program execution box, then plug in the device that needs to be added to the whitelist. When the log message "xxxx added."(xxxx is the serial number of the USB flash drive) appears, it means the adding is done. After the operation, close the command window directly and start the main process "AutoFileBAK.exe" again

#### 1.4.1.3 How to manage whitelisted devices and remove devices

The program currently does not include these features, and the development team does not have these two features on the agenda. However, it is certain that these features will be included in the next "AutoFileBAK-GUI" project. If you need to manage or remove devices from the whitelist, please manually edit the "/Setting/WhiteList.txt" file in the program directory.

### 1.4.2 Blacklist

#### 1.4.2.1 Functions of Blacklist

The white list refers to the USB devices that the program administrator does not want to backup or trust. After this device is accessed, the program will not perform any operation.

#### 1.4.2.2 How to add a device to the blacklist

First, run the "Exit all processes" script file to prevent the program from multiple executions or flashbacks.
After that, run the "Blacklist mode" script file and wait for the "Stick your USB Drive into the computer to write it into blacklist." to appear in the program execution box, then plug in the device that needs to be added to the whitelist. When the log message "xxxx added."(xxxx is the serial number of the USB flash drive) appears, it means the adding is done. After the operation, close the command window directly and start the main process "AutoFileBAK.exe" again

#### 1.4.2.3 How to manage blacklisted devices and remove devices

The program currently does not include these features, and the development team does not have these two features on the agenda. However, it is certain that these features will be included in the next "AutoFileBAK-GUI" project. If you need to manage or remove blacklisted devices, please manually edit the "/Setting/WhiteList.txt" file in the program directory.


Translated with www.DeepL.com/Translator (free version)
