# シグナル
---
//signalは、OSやユーザからprocessに送られて割り込み、終了させる。killやctrl+Cなど。

//signalの種類は、SIGABRTやSIGALRMをはじめとして、標準シグナルとリアルタイムシグナル各32種の、計64種ある。

//以下は、ctrl+\が押されるまで、メッセージを表示し続けるプログラム。
```
#include <libc.h>
void handler(int sig)
{
    fprintf(stderr, "@");
}
int main(void)
{
    signal(SIGINT, handler);
    while (1)
    {
        sleep(1);
        fprintf(stderr, "fatal error\n");
    }
    return (0);
}
```
2 SIGINT 基本動作はプロセスの終了: キーボードからの割り込みシグナル（通常は［CTRL］＋［C］）

3 SIGQUIT 基本動作は終了とコアダンプ出力: キーボードによる中止シグナル（通常は［CTRL］＋［\］）

20 SIGTSTP 基本動作はプロセス一時停止: 端末からの一時停止シグナル（通常は［CTRL］＋［Z］）

