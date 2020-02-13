# tmux 使用指南

---

1.tmux 安装

    sudo apt install tmux

---

2.tmux 快捷键

2.1 session 部分

- 新建 session

    tmux (此时名称以数字编号)	
    tmux new -s <session-name>

- 离开 session

    tmux detach
	
    ctrl + b d

- 查看 session 列表

	tmux ls

	ctrl + b s

- 进入 session

	tmux attach -t <session-name>

	tmux a -t <session-name>

- 进入上一个打开的 session

	tmux a

- 关闭 session

	tmux kill-session -t <session-name>

- 关闭上次打开的 session

	tmux kill-session

- 关闭除了某个之外的所有 session

	tmux kill-session -a -t <session_name>

- 关闭所有 session

	tmux kill-server

- 切换 session

	tmux switch -t <session-name>

- 重命名 session

	tmux rename-session -t <old-session-name> <new-session-name>

	ctrl + b $

2.2 window 操作

- 新建 window

	tmux new-window -n <window-name>

	ctrl + b c

- 切换 window

	tmux select-window -t <window-name>

	ctrl + b w (j k 上下选择，回车进入)

	ctrl + b n (下一窗口)

	ctrl + b p (上一窗口)

- 重命名 window

	tmux rename-window <new-window-name>

	ctrl + b ,

- 关闭 window

	tmux kill-window -t <window-name>

- 关闭当前 window

	ctrl + b &

- 根据显示内容搜索 window

	ctrl + b f

2.3 pane 操作

- 水平方向切割 pane

	tmux split-window -h

	ctrl + b %

- 竖直方向切割 pane

	tmux split-window

	ctrl + b "

- 不同 pane 之间移动

	tmux select-pane (-U -D -L -R)

	ctrl + b 方向键

- 切换到上一 pane 

	ctrl + b ;

- 切换到下一 pane

	ctrl + b o

- 向上移动 pane

	tmux swap-pane -U

- 向下移动 pane 

	tmux swap-pane -D

- 关闭当前 pane

	ctrl + b x

- 放大 pane

	ctrl + b z (再次按会恢复)

- pane 显示时间

	ctrl + b t

- 显示 pane 编号 

	ctrl + b q

- 显示当前 pane 信息

	ctrl + b i

2.4 其他命令

- 列出所有绑定的键

	tmux list-key

- 列出所有命令

	tmux list-command
