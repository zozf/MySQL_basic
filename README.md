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

・データベースの属性には、人工的な属性（サロゲートキー、人工キー）と自然な属性（ナチュラルキー、自然キー）がある

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