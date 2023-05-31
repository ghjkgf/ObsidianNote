### grep

记行数 
grep -c "text" file_name
记出现次数
grep -o "text" file_name | wc -l 

看目标内容上下文
grep -A 10 'NullPointerException' logback.log  // 下面10行
grep -B 10 'NullPointerException' logback.log  // 上面10行
grep -C 10 'NullPointerException' logback.log  // 上下10行

### 防火墙
ufw allow 8088
ufw delete allow 8088
ufw reload
ufw status
ufw enable/disable
ufw default deny        //拒接所有外来访问，本机能正常访问外部
ufw allow 8001/tcp            //指定开放8001的tcp协议
ufw allow from 192.168.121.1  // 指定ip为192.168.121.1的计算机操作所有端口
ufw allow from 192.168.121.2 to any port 3306  // 指定ip+port

### 安装java
mkdir /home/ubuntu/software/java
mv x.tar.gz 
tar -xzvf x.tar.gz
sudo vim /etc/profile
追加
```vim
1. JAVA_HOME=/home/ubuntu/software/java/jdk-11.0.9
2. JRE_HOME=$JAVA_HME/lib
3. PATH=$JAVA_HOME/bin:$PATH 
4. export JAVA_HOME JRE_HOME PATH
```
source /etc/profile

### 更改文件权限
chmod 777 file