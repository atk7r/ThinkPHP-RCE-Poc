# 简介
ThinkPHP 多语言模块 RCE

# 声明
此工具仅限授权安全测试使用,禁止非法攻击未授权站点

# FoFa指纹

```
header="think_lang"
```

# 漏洞信息

如果 Thinkphp 程序开启了多语言功能，攻击者可以通过 get、header、cookie 等位置传入参数，实现目录穿越+文件包含，通过 pearcmd 文件包含这个 trick 即可实现 RCE。

## 影响范围

```
v6.0.1 < Thinkphp < v6.0.13
Thinkphp v5.0.x
Thinkphp v5.1.x
```

# 使用教程

参数

```
python3 Thinkphp_Multilingual_Module_Rce.py -h

usage: Thinkphp_Multilingual_Module_Rce.py [-h] [-rh remote_host] [-f file_path] [-o outfile_path]

Thinkphp_Multilingual_Module_Rce Poc by atk7r

options:
  -h, --help            show this help message and exit
  -rh remote_host, --rhost remote_host
                        Please input host to scan.
  -f file_path, --file file_path
                        Please input file path to scan.
  -o outfile_path, --outfile outfile_path
                        Please input path and filename for output file.

```

单个扫描（一定要是ip或者域名，后面可以加端口）

```
python3 Thinkphp_Multilingual_Module_Rce.py -rh 192.168.0.1
python3 Thinkphp_Multilingual_Module_Rce.py -rh 192.168.0.1:8088

python3 Thinkphp_Multilingual_Module_Rce.py -rh www.abc.com
python3 Thinkphp_Multilingual_Module_Rce.py -rh www.abc.com:8088
```

批量扫描（url.txt的内容一定要是ip或者域名，后面可以加端口）

```
python3 Thinkphp_Multilingual_Module_Rce.py -f url.txt -o outfile.txt
```

# nuclei

```
nuclei.exe -u http://192.168.0.1:8088/ -t thinkphp-multilingual-module-rce.yaml -stats
```

# 详情

https://mp.weixin.qq.com/s/jECbQ4KodbCrEvoCQFSosw