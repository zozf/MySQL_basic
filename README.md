# MySQL_basic
MySQL の基本について

## MySQL について
・MySQL：リレーショナルデータベース（RDB）管理システムの一種

・データベース：情報を使いやすく整理整頓したものの集まり

・MySQL と MariaDB はほぼ一緒

・データ操作の基本は CRUD  
　Create（作成）  
　Read（検索）← メイン  
　Update（更新）  
　Delete（削除）

・リレーショナルデータベースの特徴  
　(1) データの強い整合性：整合性を保つ機能がある  
　(2) SQL を利用した柔軟な検索

・SQL は宣言的な言語

・Strict モード（厳格モード）：データの扱いが厳しくなる  
　DB 運用時はこのモードを使用する

・MySQL を操作するにはログインする必要がある

## MySQL 用語
・テーブル：データの集まり（表形式で管理されている）

・RDB：表形式でデータを管理するもの

・データベース：テーブルをいくつかまとめたもの

・行（ row ）が1つのデータ、列（ column ）がデータの属性  
　行はレコードとも呼ばれる  
　列は名前と、データの型からなる

・データの取得は SELECT 文で行う  
　SELECT（欲しいデータの column 名）FROM（指定したテーブル名）;  
　SELECT 文の実行結果はテーブル  
　アスタリスク（*）で全ての column を取得できる

・クエリー：データベースへの命令（SQL文）のこと

・クエリーを投げる：データベースへ命令を送ること

・MySQL の TRUE は 1 、FALSE は 0

・制限：ある条件を満たすレコードのみを取り出す操作  
　WHERE 句を使用する  
　SELECT カラム名1, カラム名2 FROM テーブル名 WHERE 条件式 ;  
　これで条件式に合致したレコードを取得できる  
　※ WHERE 句はグループ化される前に絞り込まれるため、集計関数には使用できない

・比較演算子  
　等価演算子(=)：与えられた2つの値が等しいかチェックする

・文字列型の column に対して大小比較した場合、文字列の大小関係は辞書順になる  
　column の照合順序が辞書順序の設定

・条件式を複数書く場合  
　AND  
　OR

・BETWEEN：～（以上）から～（以下）までの数値のレコードが欲しい場合に使用する  
　NOT BETWEEN で否定が可能

・IN ('文字列1', '文字列2')：OR のように書くことができて、指定する文字列に制限がない  
　NOT IN で否定が可能

・LIKE：あいまいな検索が可能  
　デフォルト状態ではケースインセンシティブ（大文字小文字を区別しない）で検索される  
　ワイルドカード文字 (%) ：あらゆる文字列の代わりになる  
　LIKE '～%'：～から始まる文字列を取得  
　LIKE '%～'：～で終わる文字列を取得  
　LIKE '%～%'：途中で～が含まれる文字列を取得

・アンダーバー（_）は何か1文字というワイルドカード文字  
　文字数が固定の場合などに便利

・ORDER BY カラム名：指定したカラム名を対象に昇順（小さい順）に並ぶ  
　文字列型に使用すると辞書順に並ぶ

・ORDER BY カラム名 DESC：指定したカラム名を対象に降順（大きい順）に並ぶ

・LIMIT：検索結果の件数を絞る  
　(例) 5件だけ絞る  
　LIMIT 5

・CREATE DATABASE データベース名：データベース作成

・CREATE TABLE テーブル名 (カラム名 データ型)：テーブル作成

・INSERT INTO テーブル名 (カラム名) VALUES (各カラムの値)：レコード作成  
　カンマ区切りで複数のレコードを一度に登録できる

・主キー：テーブル内のデータを1つ特定するための属性  
　　　　　候補キーの中から最も使いやすい属性を1つ選んで主キーとする  
　　　　　別名 Primary Key（プライマリーキー）、PK と呼ばれる  
　　　　　主キーに重複した値を入れることはできない（一意性制約）  
　　　　　主キーが空っぽのデータを登録することもできない

・候補キー：複数のデータの集まりから1つのデータを特定することができる属性  
　　　　　　候補キーは1つとは限らない

・複合キー：複数の属性を組み合わせてあるレコードを1つに特定できるような属性の集まり

・ID：idetifier = 識別子  
　　　レコードを1つに特定するためにシステムによって発行された人工的な属性  
　　　データをデータベースに登録する時に ID が決まる

・データベースの属性には、人工的な属性（サロゲートキー、人工キー）と自然な属性（ナチュラルキー、自然キ  
　ー）がある

・DROP TABLE テーブル名：テーブルの削除

・CREATE TABLE テーブル名 (  
　    カラム名1 データ型 PRIMARY KEY,  
　    カラム名2 データ型  
　);  
　で主キーを持ったテーブルの作成

・CREATE TABLE テーブル名 (  
　    カラム名1 データ型,  
　    カラム名2 データ型,  
　    PRIMARY KEY(カラム名1, カラム名2)  
　);  
　で複合キーを持ったテーブルの作成

・date 型：MySQL で日付を扱いたい時に使用する

・tinyint 型：int 型の仲間で、8 bit 整数を表し、256 種類の整数を表現することができる  
　-128 ~ 127 までの数字を表現できる  
　数字の範囲が狭いことがわかっている場合に使用する（データベースの容量を削減できる）

・コンピュータがデータを扱う時は、文字よりも数字の方が容量を節約できる  
　コンピュータ内では文字を数字に置き換えて管理している  
　文字と数字の対応表を文字コードという

・コンピュータで人の性別を扱う時の一桁の数字に関しては国際的な規格がある  
　0 : not known（不明）  
　1 : male（男性）  
　2 : female（女性）  
　9 : not applicable（適用不能）

・UPDATE テーブル名  
　SET カラム名 = 更新したい値  
　WHERE 更新したいレコードの条件  
　でデータの更新

・DELETE FROM テーブル名 WHERE 削除したいレコードの条件  
　でデータの削除

・DROP DATABASE データベース名：データベースの削除

・ROOT ユーザー：最強の権限を持ったユーザー（間違った作業を行わないように要注意）

・集計関数  
　COUNT 関数：レコードの数を数える  
　SUM 関数：カラムの合計値を求める  
　AVG 関数：カラムの平均値を求める  
　など

・SELECT SUM(カラム名) FROM テーブル名：指定したカラムの合計値を求める

・format()関数で3桁区切りの数値表現が可能

・AS 別名にしたいカラム名：AS 句を使用してカラム名に別名をつけられる

・GROUP BY 句でレコードをグループ化することができる  
　特定のカラムの値ごとに集計をしたい時に便利  
　2つ以上のカラムを指定してグループ化することも可能

・HAVING 句で集計結果がある特定の条件を満たすものだけを取得することができる  
　グループ化された後に条件で絞り込みが行われる

・JOIN：2つのテーブルを横に合体させて新しいテーブルを作る操作

・テーブル設計：どのようなデータ、テーブルを用意してアプリケーションのデータを管理するか設計する工程

・リレーションシップ：テーブル同士の繋がり

## データベースを扱う際に今後学んだ方がいいこと
1.条件分岐  
2.三値論理  
3.サブクエリを使用した複雑な SELECT 文  
4.集合論  
5.リレーショナルモデル  
6.テーブル設計（特に正規化について）  
7.インデックス設計  
8.カーディナリティ  
9.B-tree構造  
10.実行計画の見方  
11.パフォーマンスチューニング  