# 書籍: 例解UNIXプログラミング教室
---
Cの復習:  
低水準入出力:  
標準入出力ライブラリ:  
プロセス:

いくつもの同時に動いているプログラムのことを、プロセスという。
種類は、shell process, window display process, daemon等あり。  
プロセスという概念を使うと、楽にプログラムが書ける。
独自のメモリ空間内なら、プロセッサの割り当てと解放を気にせずとも良い。  
プロセスは普通1つとして動作するが、処理が複雑な際は、複数プロセスが良い場合もある。  

% echo $$  
% ps -l -p プロセスID  
例としては、プログラムは、mainから始まって、exitで終わる、などがある。  
環境変数とはプロセスに付随するデータで、プロセスは環境変数の値を読んだり、環境変数に値を設定したりできる。  
環境変数の値は文字列である。  
プロセスは、環境変数をいくつも持てる。  
環境変数とその値を表示させるには、
- コマンドenvを無引数で実行する。
- getenv("文字列")
- int main(int argc, char *argv[], char *envp[])
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
```
#include <stdio.h>
#include <stdlib.h>
int main(void)
{
	char *pathstr;
	//if ((pathstr = getenv("PATH")) != NULL)
	if ((pathstr = getenv("HOME")) != NULL)
	{
		//printf("PATH = %s\n", pathstr);
		printf("HOME = %s\n", pathstr);
	}
	else
	{
		//printf("PATH not set\n");
		printf("HOME not set\n");
	}
	return (0);
}
```
```
#include <stdio.h>
int main(int argc, char *argv[], char *envp[])
{
	int i;

	i = 0;
	while (envp[i] != NULL)
	{
		printf("%d: [%s]\n", i, envp[i]);
		i++;
	}
	return (0);
}
ファイルシステム:
ファイル記述子のコピーとパイプ:
ソケット通信入門:
シグナルと競合状態:
端末:
```
