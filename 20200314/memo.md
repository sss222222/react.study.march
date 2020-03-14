# やったこと

- React.js & Next.js 超入門の 4 章まで読んで気になるやつだけ実行した（2h くらい)
  - ちょっと内容古いかも(npx create-react-app したときの App.js が class のまま)

# わかったこと

- 書き方わからんってなってたのは JSX の構文
- 真偽値による表示の切り替えは積極的に使っていきたい

# 次にやりたいこと

- この本気になる
  - https://booth.pm/ja/items/1312652
- Redux の作り方と使い方はまとめたい
  - チュートリアルをやる？

# 学習メモ

- 実際にサーバに置くときは`npm run build`して`build`フォルダをサーバにおけば OK

## JSX

- JSX:html のタグを直接 javascript のスクリプトに記述する仕組み(babel パッケージが関連している)
  - JSX に javascript の値を埋め込むには`{変数や値}`が必要
    - `<p style={msg}>{message}</p>`
  - JSX のスタイル：スタイルシートだと`font-size`が以下のようになる

```
let printMsg = function(msg, color){
const style = {
    fontSize: "20pt",
    color: color,
    border: "1px solid " + color
};
return <p style={style}>{msg}</p>;
}
let el = (
    <div>
        {printMsg('最初のメッセージ', '#ddd')}
        {printMsg('次のメッセージです.', '#aaa')}
        {printMsg('最後のメッセージでした.', '#333')}
    </div>
);
```

- JSX の真偽値による表示の切り替え

```
let flg = true; // ★


let el = (
    <div>
    {flg ?
        <p>{true}</p>
    :
        <p>{false}</p>
    }
    </div>
);
```

- JSX の配列によるリストの表示

```
let data = [
    <li>1</li>,
    <li>2</li>,
    <li>だー</li>
];


let el = (
    <div>
        <ul style={list}>
        {data}
        </ul>
    </div>
);
```

- あらかじめ用意したデータをもとに表示する内容を作成＆繰り返し表示したいときは map
  - map:`配列.map((value)=>{新しい項目})` で配列の中身が value に渡されて、その value を元に新しい項目を作ってその配列を返すらしい
  - アロー関数：`(引数)=>{戻り値}`

```
let data = [
        { parkingName: "Sinjuku", number: 3 },
        { parkingName: "Sibuya", number: 4 },
        { parkingName: "Ikebukuro", number: 9 }
      ];
{data.map(value => (
              <tr>
                <td style={td}>{value.parkingName}</td>
                <td style={td}>{value.number}</td>
              </tr>
            ))}
```

## React コンポーネント

- 最初が大文字じゃないとコンポーネントとして認識されない

## つまづいたところ

### npx create-react-app できない…

ファイル生成が途中でつまづいて、以下のエラー文

```
A template was not provided. This is likely because you're using an outdated version of create-react-app.
Please note that global installs of create-react-app are no longer supported.
```

解決法
以下の qiita を参照

```
sudo npm uninstall -g create-react-app

```

https://qiita.com/kijibato/items/ca74c6582141f3292240
https://create-react-app.dev/docs/getting-started/
