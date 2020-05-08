# TCR practice

## TCR とは
- “test && commit || revert” by Kent Beck
    - https://medium.com/waicrew/test-commit-revert-by-kent-beck-dd2b4d52a42c

- testに失敗すると強制的にRevertする
    - `mvn test && git add . && commit -am 'working' || git reset --hard`
    - `alias=mvn test && git add . && commit -am 'working' || git reset --hard`

- 戻る歩幅が大きければ、テストの１歩が大きいというフィードバックをされることになる。

### feedBack
- Revertして戻ってしまうソースコードの量をなるべく減らしたくて、シンプルな記述に努めようとする
- testとして成り立って無くても頻繁に試そうとする


## TCRはLimboというPracticeを行うための前提となる働き方

### limbo
- https://medium.com/@kentbeck_7670/limbo-scaling-software-collaboration-afd4f00db4b
- https://medium.com/@kentbeck_7670/limbo-on-the-cheap-e4cfae840330
- 常にpullとpushをし続ける
```
while true
do
  sleep 0.5
  git pull -r
  git push
done
```

#### 生まれた背景
すごく巨大な組織の中で、円滑に開発するために出されたアイデアの種
facebookには10万人の開発者がいて、Conflictをなるべく小さく済ませるようにするためにはどうすればいいか？

