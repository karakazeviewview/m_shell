# プロセス
---
//unixシステム上で、いくつも実行されているプログラムをプロセスという。  
//getpid関数の使用例  
//psコマンドの使用例
```
#include <libc.h>
int main(void)
{
	pid_t mypid;
	char command[1024];
	
	mypid = getpid();
	printf("pid = %d\n", mypid);
	if (snprintf(command, sizeof(command), "ps -l -p %d", mypid) >= sizeof(command))
	{
		fprintf(stderr, "too long command line (pid = %d) \n", mypid);
		exit (1);
	}
	system(command);
	return (0);
}
```
//環境変数はプロセスに付随するデータで、文字列である。
//envを無引数で実行すると、環境変数たちが表示される。

//環境変数を表示するプログラム
```
#include <stdio.h>
extern char **environ;
int main(void)
{
    char **p = environ;
    while (*p != NULL)
    {
        printf("%s\n", *p);
        p++;
    }
    return (0);
}
```