# Screen 和 Tmux 常見操作對照表

## 基本終端命令

| 功能 | Screen 命令 | Tmux 命令 |
|------|------------|-----------|
| **啟動新會話** | `screen` | `tmux` |
| **啟動命名會話** | `screen -S 名稱` | `tmux new -s 名稱` |
| **分離會話** | `Ctrl+a d` | `Ctrl+b d` |
| **列出會話** | `screen -ls` | `tmux ls` |
| **重新連接會話** | `screen -r 名稱` | `tmux attach -t 名稱` |
| **重新連接會話（如在用則強制附加）** | `screen -dr 名稱` | `tmux attach -d -t 名稱` |
| **刪除會話** | `screen -X -S 名稱 quit` | `tmux kill-session -t 名稱` |
| **刪除所有會話** | `pkill screen` | `tmux kill-server` |
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
| **重新載入配置** | N/A | `tmux source-file ~/.tmux.conf` |
| **命令模式** | `Ctrl+a :` | `Ctrl+b :`

## 進階終端設定命令

## 終端命令列參數和進階設置

| 功能 | Screen 命令 | Tmux 命令 |
|------|------------|-----------|
| **指定配置文件** | `screen -c 配置檔案路徑` | `tmux -f 配置檔案路徑` |
| **指定套接字路徑** | `screen -S 套接字名稱/路徑` | `tmux -S 套接字路徑` |
| **在新窗口中啟動命令** | `screen 命令` | `tmux new-session 命令` |
| **指定視窗大小** | N/A | `tmux new -x 寬度 -y 高度` |
| **設置環境變數** | `screen -e 變數` | N/A |
| **指定日誌文件** | `screen -L -Logfile 檔案名稱` | `Ctrl+b :pipe-pane -o 'cat >> 檔案名稱'` |
| **多用戶模式** | `screen -x 會話名稱` | `tmux -S /tmp/shared attach` (需設置權限) |
| **查看會話資訊** | `screen -ls` | `tmux info` |
| **啟動UTF-8支持** | `screen -U` | 默認啟用 |
| **靜默模式啟動** | `screen -q` | N/A |
| **在後台啟動新會話** | `screen -dm -S 會話名稱` | `tmux new -d -s 會話名稱` |
| **向會話發送命令** | `screen -S 會話名稱 -X 命令` | `tmux send-keys -t 會話名稱 "命令" C-m` |
| **鎖定會話** | `Ctrl+a x` | `Ctrl+b :lock-session` |
| **將窗口分離到新會話** | N/A | `tmux break-pane -s 窗口名稱` |
| **移動窗口** | `Ctrl+a :number 新編號` | `tmux move-window -t 新編號` |
| **調整面板大小** | `Ctrl+a :resize` | `Ctrl+b :resize-pane -D/U/L/R 行數` |
| **顯示所有按鍵綁定** | `Ctrl+a ?` | `Ctrl+b ?` |



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

### 長時間運行任務的最佳實踐
```bash
# 使用 Screen
screen -S 任務名稱 -L -Logfile ~/任務名稱.log
# 執行長時間任務
命令 > ~/任務名稱.out 2>&1
# 按 Ctrl+a d 分離

# 使用 Tmux
tmux new -s 任務名稱
# 執行長時間任務
命令 > ~/任務名稱.out 2>&1
# 按 Ctrl+b d 分離
```

大多數情況下，您只需記住 Screen 使用 `Ctrl+a` 作為前綴鍵，而 Tmux 使用 `Ctrl+b`，然後大部分操作都非常相似。最常用的命令是啟動會話、分離會話和重新連接會話，這些在兩個工具中的概念都是一致的。
