# 目的
早い！安い！うまい！今日の献立を決めてくれるアプリの開発。
仕事で忙しい中、手料理を振る舞っている方の助けになればと思い作成。

## 使い方
完成次第記述。

## こだわったポイント
完成次第記述。

## 使用言語
- Ruby
- Java script

## フレームワーク
- Ruby on rails
- Jquery


# テーブル設計

## usersテーブル

| Column             | Type    | Options                   |
| ------------------ | ------- | ------------------------- |
| nickname           | string  | null: false               |
| email              | string  | null: false, unique: true |
| encrypted_password | integer | null: false               |

### Association
- has_many :menus
- has_many :comments

## menusテーブル

| Column    | Type       | Options                        |
| --------- | ---------- | ------------------------------ |
| title     | string     | null: false                    |
| recipe    | text       | null: false                    |
| user      | references | null: false, foreign_key: true |

### Association
- belongs_to :user
- has_many :foodstuffs_menus
- has_many :foodstuffs, through: foodstuff_menus
- has_many :menu_tags
- has_many :tags, through: menu_tags
- has_many :comments

## commentsテーブル

| Column   | Type       | Options                        |
| -------- | ---------- | ------------------------------ |
| comment  | string     |                                |
| user     | references | null: false, foreign_key: true |
| menu     | references | null: false, foreign_key: true |

### Association
- belongs_to :user
- belongs_to :menu

## foodstuffsテーブル

| Column         | Type       | Options                        |
| -------------- | ---------- | ------------------------------ |
| foodstuff_name | string     | null: false                    |
| quantity       | string     | null: false                    |
| serving        | integer    | null: false                    |
| menu           | references | null: false, foreign_key: true |

### Association
- has_many :menus, through: foodstuff_menus
- has_many :foodstuff_tags

## foodstuff_menusテーブル

| Column      | Type       | Options                        |
| ----------- | ---------- | ------------------------------ |
| foodstuff   | references | null: false, foreign_key: true |
| menu        | references | null: false, foreign_key: true |

### Association
- belongs_to :foodstuff
- belongs_to :menu

## menu_tag_relationsテーブル

| Column   | Type       | Options                        |
| -------- | ---------- | ------------------------------ |
| menu     | references | null: false, foreign_key: true |
| tag      | references | null: false, foreign_key: true |

### Association
- belongs_to :menu
- belongs_to :tag

## tagsテーブル

| Column   | Type   | Options     |
| -------- | ------ | ----------- |
| name     | string | null: false |

### Association
- has_many :menu_tags
- has_many :tags, through: menu_tags

