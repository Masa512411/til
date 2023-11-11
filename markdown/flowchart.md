## mermaidでフローチャート
### 方向
- フローチャートを書く際は`graph`と書いて、後ろで方向をしてする

| 方向  | オプション |
|---|:-:|
|  上 → 下  |  TB, TD  |
|  下 → 上  |  BT  |
|  右 → 左 |  RL |
|  左 → 右  |  LR  |

#### 上から下
```mermaid
graph TB
    A --> B
```
#### 下から上 
```mermaid
graph BT 
    A --> B
```
#### 右から左
```mermaid
graph RL 
    A --> B
```
#### 左から右
```mermaid
graph LR 
    A --> B
```
--- 
## 書き方の基本
1.  Aという名前のノードを作成し、表示
```
graph RL
    A
```
```mermaid
graph RL
    A
```
2. テキストを設定する場合は`[]`ないに書く

```
graph RL
    A["スタート"]
```
```mermaid
graph RL
    A["スタート"]
```

### ノードの繋ぎ方
#### 矢印で結ぶ
- AとBのノードを繋ぐには矢印で結ぶことができる

```mermaid
graph LR
    A --> B
```
#### 矢印上にテキスト表示
- 矢印上のテキスト表示には矢印の間に記入

```
graph LR
    A -- "こんにちは" --> B
```

```mermaid
graph LR
    A -- "こんにちは" --> B
```
#### 線で結ぶ
- ノード間を線で結ぶ場合はハイフン3つ
```
graph LR
    A--B
```
```mermaid
graph LR
    A---B
```
#### 点線矢印
- 間にドットを挟
```
graph LR
    A -.-> B
```
```mermaid
graph LR
    A -.-> B
```
#### 太い矢印
- ハイフンでなく`=`で結ぶ
```
graph LR
    A ==> B
```
```mermaid
graph LR
    A ==> B
```
間にテキストも挟める
```mermaid
graph LR
    A =="おはよう"==> B
```
## ノードの形
#### ノードの角を丸める
- テキストを括弧で囲む
```
graph LR
    A("Start")
```
```mermaid
graph LR
    A("Start")
```

## 丸
- 二重括弧で円
```
graph LR
    A(("Start"))
```
```mermaid
graph LR
    A(("Start"))
```
## 左右非対称

```
graph LR
    A>"おはよう"]
```
```mermaid
graph LR
    A>"おはよう"]
```
## 菱形
- 鉤括弧で菱形

```
graph LR
    A{"Text"}
```
```mermaid
graph LR
    A{"Text"} 
```

## 円柱
- `[()]`
```
graph LR
    A[("DataBase")]
```
```mermaid
graph LR
    A[("DataBase")]
```
---
### 例
```mermaid

flowchart TB
    Start --> Tsk1
    Tsk1{"分岐"} --> Task2
    Tsk1 -->Task3
    Task2---Task3

```

