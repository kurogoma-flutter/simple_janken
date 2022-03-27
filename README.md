# janken_game

じゃんけんアプリです。
10連勝目指してください。

## 画面

<table>
  <tr>
    <th>トップ</th>
    <th>結果画面</th>
    <th>あいこの時①</th>
    <th>あいこの時②</th>
  </tr>
  <tr>
    <td>
      <img width="300" src="https://user-images.githubusercontent.com/67848399/159233248-dbc570f6-5f18-4625-b97d-ba8839263950.png">
    </td>
    <td>
      <img width="300" src="https://user-images.githubusercontent.com/67848399/159233268-3d39866a-9d24-4e43-897f-7c98c0a2db1a.png">
    </td>
    <td>
      <img width="300" src="https://user-images.githubusercontent.com/67848399/159233285-4aac75f7-4ba3-4347-810b-bbd61b47782d.png">
    </td>
    <td>
      <img width="300" src="https://user-images.githubusercontent.com/67848399/159233282-a6a491bf-ee57-46ec-a07a-426073ec229b.png">
    </td>
  </tr>
</table>

## 主要ロジック
### 3種類以上の切り替えをしたい時
基本的にウィジェットのプロパティには、三項演算子を用いればオンオフ程度の切り替えはできる。
```dart
color: index == 1 ? Colors.red : Colors.blue;
```
しかし、３種類以上となるとシンプルにはできない。<br>
その対策として、メソッドを用意してあげることで３種類以上の分岐も可能となる
```dart
  //　引数として受け取る
  final int index;

  // 色の分岐
  _cardColor() {
    switch (index) {
      case 0:
        return Colors.red;
      case 1:
        return Colors.orange;
      case 2:
        return Colors.blueAccent;
    }
  }
  
// 呼び出し
color: _cardColor()
```
### あいこ処理
あいことなった場合、`_isAiko`という変数をtrueにすることであいこかどうかを判定。<br>
あとはそれぞれのウィジェットで以下のようにして切り替えをする
```dart
child: RetryCard(content: _isAiko == true ? 'あいこ' : 'もう一回遊ぶ!'),
```

