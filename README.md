# README

# テーブル設計

## users テーブル

| Column   | Type   | Options     |
| -------- | ------ | ----------- |
| nickname | string | null: false |
| email    | string | null: false |
| password | string | null: false |

### Association

- has_one  :questions
- has_many :room_users
- has_many :rooms, through: :room_users
- has_many :messages

## questions テーブル

| Column        | Type       | Options     |
| ------------- | ---------- | ----------- |
| philosophy_id | integer    | null: false |
| color_id      | integer    | null: false |
| my_type_id    | integer    | null: false |
| like_type_id  | integer    | null: false |
| prefecture_id | integer    | null: false |
| food_id       | integer    | null: false |
| hobby_id      | integer    | null: false |
| music_id      | integer    | null: false |
| angry_id      | integer    | null: false |
| improve_id    | integer    | null: false |
| user          | references |             |

## Association

- belongs_to :user, optional: true

## rooms テーブル

| Column | Type   | Options     |
| ------ | ------ | ----------- |
| name   | string | null: false |

### Association

- has_many :room_users
- has_many :users, through: :room_users
- has_many :messages


## room_users テーブル

| Column | Type       | Options                        |
| ------ | ---------- | ------------------------------ |
| user   | references | null: false, foreign_key: true |
| room   | references | null: false, foreign_key: true |

### Association

- belongs_to :room
- belongs_to :user

## messages テーブル

| Column  | Type       | Options                        |
| ------- | ---------- | ------------------------------ |
| content | string     |                                |
| user    | references | null: false, foreign_key: true |
| room    | references | null: false, foreign_key: true |

### Association

- belongs_to :room
- belongs_to :user