# telegram_channel_downloader
Telegram 频道/群组 文件下载脚本

脚本需要python3环境，具体安装教程自行搜索。

测试环境  Ubuntu 18.04.5 LTS & Python 3.6.9

**1. 前提**
 
 - 从 https://my.telegram.org/apps 获取自己的Telegram API密钥。

 - 下载脚本
 ```
 git clone https://github.com/snow922841/telegram_channel_downloader.git
 ```
 
 - 安装fclone（可选）
 ```
 wget https://github.com/mawaya/rclone/releases/download/fclone-v0.4.1/fclone-v0.4.1-linux-amd64.zip -O fclone.zip && unzip fclone.zip && mv fclone*/fclone /usr/bin && chmod +x /usr/bin/fclone && fclone version
 ```

**2. 使用**

 - 进入脚本目录
 ```
 cd telegram_channel_downloader
 ```
 - 安装依赖 
 
 ```
 pip3 install -r requirements.txt
 ```

 - 修改telegram_channel_downloader.py文件内的 api_id 和 api_hash 为你自己的

 - 修改脚本内的bot_token 、 admin_id等必填配置
 
 - 鉴于网友需要上传GD，特添加了使用gclone自动上传到团队盘的功能，需要在配置区域设置。具体查看脚本内注释
   
 - 运行  
 ```
 python3 tg_channel_downloader.py
 ```
 - 按照提示输入telegram绑定的手机号获取验证码并输入
 
 - 配置完成后需要给bot发送 /start 频道的链接 0 才会正式开始运行脚本，否则无法启动 0代表开始下载消息的ID，可以自行修改。

 **3. 常见问题**
 
 - 关于获取admin_id
  
  可以在电报中给@get_id_bot这个bot发消息获取
 
 - 关于上传到OneDrive
  
  在脚本中找到一下参数：drive_id=''，drive_name='onedrive'， onedrive 就是你配置rclone的时候填的盘名称， 还有102行的fclone替换为rclone，rclone需要自行安装。

<details>
  <summary>点击查看更新日志</summary>
 
  2020-09-15更新
  
   - 移除下载上传进度条显示。
   
   - 使用异步并发，默认10个任务同时进行。
   
   - 修复异常重试
   
   - 远程添加任务，方便下载多个频道消息。
   
   - 移除redis保存任务
   
   - 增加全部频道、群组新消息监控，请在配置区域自行修改。
    
  2020-09-03更新
  
   - ref超时异常自动重试
  
  2020-09-01更新
  
   - 使用bot启动，并使脚本持久化，
   
   - 优化代码
   
   - 修复一些bug
  
  2020-08-29更新
  
   - 更换telegram的第三方库
  
   - 默认上传到GD，目前未配置不上传，所以需要安装gclone
  
   - 默认过滤贴纸、动态贴纸、gif格式文件
  
   - 优化了下载和上传进度条的显示
  
   - 上传失败后会把消息ID保存在脚本所在的文件夹，方便以后可以手动下载
  
  2020-08-19更新
     
   - 添加自动上传到Googledrive的功能
     
   - 使用redis缓存已经遍历的消息ID
 
</details>
