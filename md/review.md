bin/ls OK  
空でls OK  
ls+タブのみ ng(挙動が違う。課題に追加済み) NG

bin/ls ""や''でくくる、またはくくらない OK

echo  
echo 引数有り、または引数なし OK  
echo -n 引数 OK

<br>
exit  

exit 引数有り、または引数なし OK  
minishellの再立ち上げ OK

<br>
/bin/ls など実行し、""や''なしで echo $ナントカ がbashと同じか? OK

<br>
'/bin/ls filethatdosenotexist'のような失敗するはずのコマンドの動きは? ng(エラーメッセージが出ない) NG

<br>
expr $?+$? ng(クラッシュする) NG

<br>
signal

空のプロンプトでctrl-Cを実行すると、新プロンプトが表示され改行されるか? ng(^Cと表示。改行されない) NG

空のプロンプトでctrl-\を押すとbashと同じく無反応か? ng(^\と出てしまう) NG

空のプロンプトでctrl-Dを押すと終了するか? OK

プロンプトでctrl-Cを押すと改行されて新プロンプトが表示されるか? ng(^Cと出てしまう) NG

プロンプトでctrl-Dを押すと、なにも起こらないか? OK

プロンプトでctrl-\を押すとbashと同じく無反応か? ng(^\と出てしまう) NG

引数なしでcatやgrepなどのブロッキングコマンドを実行し、ctrl-Cでの挙動は? ng(終了しない) NG

<br>
引数なしでcatやgrepなどのブロッキングコマンドを実行し、ctrl-\での挙動は? ng(^\が出て終了しない) NG

引数なしでcatやgrepなどのブロッキングコマンドを実行し、ctrl-Dでの挙動は? OK

<br>
double quote

引数をダブルクウォートと空白" "で、$を使わず以下の様に何らかのコマンドを実行。挙動は? OK

echo "cat lol.c | cat > lol.c" OK

<br>
single quote

引数をシングルクウォートで囲んだコマンドの実行。挙動は? OK

空の引数を渡した時の挙動は? OK

環境変数、空白文字、パイプ、をシングルクウォートで試す。挙動は? OK

echo '$USER'は$USERを表示するか? OK

シングルクォート''で囲むと本来解釈できないものは、挙動がbashと一致するか? ng('cat noexist'でエラーが出ない) NG

<br>
env

envで現在の環境変数が表示されているか? OK

<br>
export

環境変数をexportし、新しい変数を作成。古い変数は置き換えて、envで確認する。 ng(MM="mmatsuo"と打つと、MM=""とmmatsuo=""との2個に分かれてしまう)

<br>
unset

一部の環境変数を削除するにはunsetを使い、envで結果を確認する。OK

<br>
cd

作業ディレクトリを移動し、/bin/lsで正しいディレクトリにいるかを確認する。 NG

動作するはずのcdと動作しないはずのcdを複数回ためす。

引数として、'.', '...'も試す。

<br>
pwd

複数のディレクトリで、pwdを複数回試す。 ng(cd完成後に要挙動再チェック!!) NG

<br>
Relation Path

相対パスを使用してコマンドを実行する。

たくさんの'..'を使用した複雑な相対パスで、複数のディレクトリで複数回コマンド実行する。 OK

<br>
Environment Path

コマンドを実行するが、今回はパスを指定しない。

PATHの設定を解除し、動作しなくなったかどうかを確認する。 OK

PATHに複数ディレクトリの値(directory1: directory2)を設定し、左から順番にディレクトリがチェックされることを確認する。

<br>
redirection

<, > を使って、コマンドを実行する。 OK

コマンドや引数を変えて複数回繰り返し、> を >> にも変更してみる。

同じリダイレクトが複数回失敗するかどうかをチェックする。

<< のリダイレクトをテストする(履歴更新の必要はない) OK

<br>
pipe

'cat file | grep bla | more' のようにパイプでコマンド実行する。

コマンドと引数を変えて複数回繰り返す。

'ls filethatdoesntexist | grep bla | more' のような失敗するはずのコマンドを試す。 OK

パイプとリダイレクトを混ぜてコマンド実行する。 ng(echo 'a' > out | echo 'b' >> out | echo 'c' >> out | echo 'd' >> out | cat 'out' の挙動が違う)

<br>
Go Crazy and history

コマンドラインを入力し、Ctrl-Cを押し、Enterを押すと、バッファは綺麗になり、なにも実行されないか確認する。 ng(空行が入ってしまう) NG

履歴を上下に移動して、過去実行したコマンドを再試行できるか確認する。 OK

'dsbksdgbksdghsd'のような動作しないはずのコマンドを実行し、クラッシュしないかを確認する。 ng(command not foundのエラーメッセが出ない) NG

大量の引数を持つ長いコマンドを実行してみる。

<br>
Environment Valiables

いくつかの$変数を引数としてechoを実行する。 ng(echo $$USERでクラッシュする。echo $USER $TERMはOK) NG

環境変数として$が解釈されることを確認する。 OK

ダブルクォートが$を補完していることを確認する。 OK

USERが存在するか、設定されているかを確認する。 OK

echo "USER" は、bashと同じ値を表示するか確認する。 OK

<br>
Mandatoryは以上。

