# テーブル設計

## users テーブル

| Column              | Type   | Options                   |
| ------------------- | ------ | ------------------------- |
| email               | string | null: false, unique: true |
| encrypted_password  | string | null: false               |
| nickname            | string | null: false               |

### Association

- has_many :room_users
- has_many :rooms, through: room_users
- has_many :chats


## rooms テーブル

| Column | Type   | Options     |
| ------ | ------ | ----------- |
| title  | string | null: false |

### Association

- has_many :room_users
- has_many :users, through: room_users
- has_many :chats


## room_users テーブル

| Column | Type       | Options                        |
| ------ | ---------- | ------------------------------ |
| user   | references | null: false, foreign_key: true |
| room   | references | null: false, foreign_key: true |

### Association

- belongs_to :room
- belongs_to :user


## chats テーブル

| Column  | Type       | Options                        |
| ------- | ---------- | ------------------------------ |
| content | string     |                                |
| user    | references | null: false, foreign_key: true |
| room    | references | null: false, foreign_key: true |

### Association

- belongs_to :room
- belongs_to :user