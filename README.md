1. 第一步:
    - 设置-订阅-右上'+'-服务器
    - 名称(自己命名)
    - 链接(复制下面,ps:我的服务器卡)```https://raw.githubusercontent.com/Rogershanyu/QuantumultX/master/NMQ```
    - 保存
2. 第二步:
    - 设置-分流-右上'+'
    - 类型:user-agent
    - 行为:选择第一步添加的服务器(建议选上海节点)
    - 匹配:NeteaseMusic*
    照上面方法把下面的都添加了
    ```
    类型,行为,匹配
    user-agent,节点名称,NeteaseMusic*
    user-agent,节点名称,NeteaseMusic**
    user-agent,节点名称,网易云音乐*
    user-agent,节点名称,网易云音乐**
    user-agent,节点名称,%E7%BD%91%E6%98%93%E4%BA%91%E9%9F%B3%E4%B9%90*
    user-agent,节点名称,%E7%BD%91%E6%98%93%E4%BA%91%E9%9F%B3%E4%B9%90**
    ```
3. 第三步
    - 设置-运行模式-自动分流
    - 首页-右上角打开
