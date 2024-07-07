# 画面を戻った際に再描画する方法

### Navigator.pop()で画面を戻って来たときに再描画したい

### 方法

1. onPressed などで画面遷移をする処理を async で記述する。(pop した際はここに戻る)
2. await で Navigator.push()を呼ぶことで、画面が戻ってくるまでここで待ち続ける。
3. 戻ってきたら、setState や notifyListeners()で再描画を行う。

Navigator.pop()で値を返せるので、呼び出しもとに値を渡せる。

### 例

Navigator.of(context).push を await で実装する。

```
  void textEditorPageWithReloadByReturn(BuildContext context) async {
    final result = await Navigator.of(context)
        .push(MaterialPageRoute(builder: (context) => const TextEditorPage()));
    if (result != null) {
      refreshList();
    }
  }

```

```
  onPressed: () {
    textEditorPageWithReloadByReturn();
  },
```

pop で true を渡す。

```
  Future<void> _docSave(QuillController controller, context) async {
    final db = Localstore.instance;

    final json = controller.document.toDelta().toJson();
    final id = db.collection('doc').doc().id;
    final flag = controller.document.toPlainText().trim().isEmpty;

    await db.collection('todos').doc(id).set(json[0]);
    Fluttertoast.showToast(msg: '保存しました。$flag');
    Navigator.of(context).pop(true);
  }
```

#### 参考

https://docs.flutter.dev/cookbook/navigation/returning-data

NavigatorObserver を使って didPop
