# gobang-client
这个应用程序被用于五子棋对战，要有服务器获取玩家列表，进行连接才能正常使用

设计
连接过程：
Client:（QT）
1.	连接服务器
2.	显示连接状态 --- 如果连接成功转3；否则，显示连接失败
3.	获取玩家列表
4.	监听是否有玩家新上线 --- 如果有，添加到玩家列表
5.	发送邀请信息 --- 选择玩家，发送到服务器，转8
6.	 接收服务器邀请信息 --- 接收到玩家信息（游戏套接字），选择是否接受，并发回。如接受转7
7.	 连接邀请方 --- 根据收到的玩家信息，连接邀请方。如失败，返回服务器。
8.	监视连接结果 --- “拒绝”|“对方连接错误”
9.	游戏对战（聊天）
10.	断开游戏连接
11.	断开服务器连接

对战过程：
1.	选择黑子，白子 --- 受邀方选择
2.	接受对方落子坐标，并存储，转4
3.	己方落子并发送，存储并转发，转4
4.	判断胜负 --- 已定，本局结束；否则，等待对方落子
