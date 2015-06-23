# ターミナルのプロンプトにブランチ名を表示させる。

## 手順

1. ホームに移動
<pre>
$ cd
</pre>

2. ファイルを取得
<pre>
$ wget https://raw.github.com/git/git/master/contrib/completion/git-completion.bash
$ wget https://raw.github.com/git/git/master/contrib/completion/git-prompt.sh
</pre>

3. 隠しファイルに変更
<pre>
$ mv git-completion.bash .git-completion.bash
$ mv git-prompt.sh .git-prompt.sh
</pre>

4. .barshrcに以下を追加
```bash
if [ -f ~/.git-completion.bash ]; then
    source ~/.git-completion.bash
fi

if [ -f ~/.git-prompt.sh ]; then
    source ~/.git-prompt.sh
fi

PS1="[@\u:\W\$(__git_ps1)]\$ "
```
