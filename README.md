# Screen-and-Tmux
A cheat sheet to help me familiarize myself with the relevant commands

# Screen 和 Tmux 常見操作對照表

| 功能 | Screen 命令 | Tmux 命令 |
|------|------------|-----------|
| **啟動新會話** | `screen` | `tmux` |
| **啟動命名會話** | `screen -S 名稱` | `tmux new -s 名稱` |
| **分離會話** | `Ctrl+a d` | `Ctrl+b d` |
| **列出會話** | `screen -ls` | `tmux ls` |
| **重新連接會話** | `screen -r 名稱` | `tmux attach -t 名稱` |
| **刪除會話** | `screen -X -S 名稱 quit` | `tmux kill-session -t 名稱` |
| **建立新視窗** | `Ctrl+a c` | `Ctrl+b c` |
| **切換下一個視窗** | `Ctrl+a n` | `Ctrl+b n` |
| **切換上一個視窗** | `Ctrl+a p` | `Ctrl+b p` |
| **切換到指定視窗** | `Ctrl+a [0-9]` | `Ctrl+b [0-9]` |
| **視窗列表** | `Ctrl+a "` | `Ctrl+b w` |
| **水平分割視窗** | `Ctrl+a S` | `Ctrl+b "` |
| **垂直分割視窗** | `Ctrl+a \|` (需配置) | `Ctrl+b %` |
| **在面板間移動** | `Ctrl+a [Tab]` | `Ctrl+b [方向鍵]` |
| **關閉當前面板/視窗** | `Ctrl+a k` 或 `exit` | `Ctrl+b x` 或 `exit` |
| **進入捲動模式** | `Ctrl+a [` | `Ctrl+b [` |
| **退出捲動模式** | `ESC` | `q` |
| **重命名當前視窗** | `Ctrl+a A` | `Ctrl+b ,` |
| **顯示時間** | `Ctrl+a t` | `Ctrl+b t` |
| **重新載入配置** | N/A | `Ctrl+b :source-file ~/.tmux.conf` |
| **命令模式** | `Ctrl+a :` | `Ctrl+b :` |

## 基本使用流程對照

### Screen 基本使用流程
1. 啟動會話：`screen -S 工作名稱`
2. 執行命令和程序
3. 分離會話：`Ctrl+a d`
4. 重連會話：`screen -r 工作名稱`

### Tmux 基本使用流程
1. 啟動會話：`tmux new -s 工作名稱`
2. 執行命令和程序
3. 分離會話：`Ctrl+b d`
4. 重連會話：`tmux attach -t 工作名稱`

大多數情況下，您只需記住 Screen 使用 `Ctrl+a` 作為前綴鍵，而 Tmux 使用 `Ctrl+b`，然後大部分操作都非常相似。最常用的命令是啟動會話、分離會話和重新連接會話，這些在兩個工具中的概念都是一致的。
