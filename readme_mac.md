## 安装虚拟环境（可选）
### 安装python3.8.* & pip
https://bootstrap.pypa.io/get-pip.py
python3 get-pip.py

### 添加虚拟环境扩展包
pip3 install virtualenv

### 创建虚拟环境
python3 -m venv .venv

### 激活虚拟环境 Mac
source .venv/bin/activate


## 导入项目 (在项目根目录下执行,需要配好python环境)
python ./require/setup.py install

## 导入依赖
pip3 install -r requirements.txt

## 现存依赖写入依赖管理
pip3 freeze>requirements.txt

## 配置

配置文件的模板在根目录的`config-template.json`中，需复制该模板创建最终生效的 `config.json` 文件：

```bash
cp config-template.json config.json
```

然后在`config.json`中填入配置，以下是对默认配置的说明，可根据需要进行自定义修改：

```bash
# config.json文件内容示例
{ 
  "open_ai_api_key": "YOUR API KEY"                           # 填入上面创建的 OpenAI API KEY
  "single_chat_prefix": ["bot", "@bot"],                      # 私聊时文本需要包含该前缀才能触发机器人回复
  "single_chat_reply_prefix": "[bot] ",                       # 私聊时自动回复的前缀，用于区分真人
  "group_chat_prefix": ["@bot"],                              # 群聊时包含该前缀则会触发机器人回复
  "group_chat_keyword": ["为什么", "why", "Why", "?", "请教"], # 群聊内容包含其中任意字符串，将会触发机器人回复
  "group_name_white_list": ["ChatGPT测试群", "ChatGPT测试群2"], # 开启自动回复的群名称列表
  "group_name_keyword_white_list": ["相亲相爱", "瞎侃"],       # 开启自动回复的群名称关键字列表（群名称含关键字即可匹配上）
  "image_create_prefix": ["画", "看", "找"]                    # 开启图片回复的前缀
}
```