# <center>数仓与ETL问答机器人</center>

<center>李军利 / 2019-01-10</center>

<center>分类：编程，算法，NLP，问答机器人</center>

<center>关键词：智能问答，分词，关键词匹配，相似度，Flask, Gunicorn</center>





## <center>项目背景</center>

​	回答数仓与ETL群里的问题占用开发人员大量的时间，构建的常见问题文档篇幅又过大，群里问题还是应接不暇，公司已有的自动问答系统专业性不够强，需要做一个适用的自动问答系统。问答数据的处理与算法都是用Python，而且智能问答系统仅供内部使用，并发量不是很大，所以服务端直接采用 Python 的 Flask 框架构建，生产环境里使用Gunicorn启多进程。常见问题的数据量用深度学习不足以训练出非常好的算法，问题的专业性又很强，所以关键词匹配算法是一个简单合适的选择。



## <center>代码目录结构</center>

```
jdd-etl-qa-produce/                # 工程根目录
├── bin/                           # 可执行命令目录
|   ├─ start.sh                    # 启动脚本
|   ├─ stop.sh                     # 停止脚本
|   └─ env.sh                      # 安装环境
├── static/                        # 前端目录
|   ├─ css
|   ├─ js
|   └─ ...
├── docs/api.md                    # 接口文档
├── jdd_etl_qa/                    # 模块根目录
|   ├─ conf/                       # 日志目录
|   |   ├─ __init__.py
|   |   ├─ log.conf                # 日志参数
|   |   ├─ read_logger.py          # 打印日志
|   |   └─ ...
|   ├─ core/                       # 模型代码根目录
|   |   ├─ __init__.py
|   |   ├─ qa_system.py            # 计算问题相似度
|   |   └─ ...
|   ├─ data/                       # 数据根目录
|   |   ├─ qa_data                 # 本地数据根目录
|   |   |   ├─ customise.txt       # 自定义专业词语
|   |   |   ├─ Question_list.txt   # 历史问题列表
|   |   |   ├─ Superword_list.txt  # 重要词汇列表
|   |   |   ├─ QA_dict.json        # 历史问答对字典
|   |   |   ├─ question_key.json   # 历史问题及关键词字典
|   |   ├─ __init__.py
|   |   ├─ read_local_data.py      # 读入本地数据
|   ├─ model/model_resource.py     # 回答post过来的问题
|   ├─ validation/                 # 校验json格式包 
├── .gitignore                     # Git Ignore 文件
├── main.py                        # 主程序代码
├── README.md                      # 说明文件
└── requirements.txt               # 依赖包列表
```





## <center>数据准备</center>

​        下载群历史聊天记录，将聊天数据结构化，提取有用问答对及关键词，以列表和字典形式存储问答数据



## <center>算法</center>

​        给予关键词不同的权重，问题分词，关键词匹配算法计算相似度，输出答案



## <center>推荐工具</center>

​        此算法可能适用于其他很多特定领域的自动问答，如果读者(尤其是像我这样的学生)有兴趣，使用自己的笔记本电脑就能模拟自动问答系统，代码和数据涉及公司机密，就不分享了，下面是给学生党推荐的一些工具：

​	**Pycharm**: 功能强大的Python IDE，与Github关联方便，可以连通Anaconda的包，免去下载包的麻烦

​	**Postman**: 伪装post请求，测试模型，用于Google浏览器，Firefox用户可使用**RESTClient**插件

​	**VirtualBox**: 比VMvare player小巧灵活，系统安装**CentOS-Minimal**版本即可

​	**FindShell**: 界面比虚拟机更加友好，方便系统之间互传文件，相比Xshell，最大优势是免费


