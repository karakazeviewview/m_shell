# 使用可能関数を使ったサンプルコード
---
- execve
```
#include <sys/types.h>
#include <errno.h>
#include <fcntl.h>
#include <pthread.h>
#include <signal.h>
#include <stdio.h>
#include <stdlib.h>
#include <unistd.h>
static void mask_sigchld(void)
{
    sigset_t sigset;
    sigemptyset(&sigset);
    sigaddset(&sigset, SIGCHLD);
    pthread_sigmask(SIG_BLOCK, &sigset, NULL);
}

static void unmask_sigchld(void)
{
    sigset_t sigset;
    sigemptyset(&sigset);
    sigaddset(&sigset, SIGCHLD);
    pthread_sigmask(SIG_UNBLOCK, &sigset, NULL);
}

int main(int argc, char *argv[])
{
    pid_t pid;
    //char *argv;
    extern char **environ;

    mask_sigchld();

    pid = fork();
    if (pid > 0)
    {
        write(1, "parent process\n", 15);
    }
    else if (pid == 0)
    {
        write(1, "child process\n", 14);
        int i;
        for (i = 3; i < 1024; i++)
        {
            close(i);
        }
        argv[0] = "echo";
        argv[1] = "Hello World!";
        argv[2] = NULL;

        execve("/bin/echo", argv, environ);
        perror("execve");
        _exit (0);
    }
    else
    {
        perror("fork");
    }
    unmask_sigchld();
    return (0);
}
```
//sigset_t:

//引数

//fillepath: プログラムつまり実行バイナリorスクリプトファイルのパス   
//argv: プログラムに渡す引数の配列

//envp: プログラムに渡す環境変数の配列


//戻り値

//成功時はリターン無し、execve失敗時は-1

//引数は必ず、(char **argv, char **envp) の形でパスされてくる。