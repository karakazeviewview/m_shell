# Doxygenによるドキュメント化
---
# Doxygenとは
C言語に対応したドキュメント生成ツール。
ソースコードの構造やUML図がHTML形式で出力できます。  
<br>
# インストール方法（mac） 
1. Homebrewで簡単  
```brew install doxygen```  
```brew install graphviz```  
→ graphvizは任意だが、インストールするとUML図が出力できる。  
<br>
2. プロジェクト直下で以下のコマンドを入力。  
```doxygen -g```  
→Doxfileが作成される。  
<br>
3. 以下コマンドを入力  
```doxygen```  
Doxyfileをもとにドキュメントが生成される。  
<br>
4. VSCodeの拡張機能  
[Doxygen Documentation Generator](https://marketplace.visualstudio.com/items?itemName=cschlosser.doxdocgen)をインストールしておくと便利  
<br>
# 記述方法  

## フォーマット例  
```
/** こんな感じのコメントが認識される */  
```
```
/*  
** こんな風に  
** 複数行でも  
** 認識される  
*/
```
## ファイルの記述例  
```
/**  
* @file ファイル名.h  
* @brief 簡単な説明  
* @author 作成者  
* @date 作成日  
* @details 詳細な説明  
*/  
```
## 関数の記述例  
```
/**  
* @brief 簡単な説明（～する関数）  
* @param[in] a(引数名) 引数の説明  
* @param[out] b(引数名) 引数の説明  
* @return bool 戻り値の説明  
* @details 詳細な説明  
*/  
```
# Doxyfileの推奨設定  