# テーブル設計

## users テーブル

| Column             | Type         | Options                        |
| ------------------ | ------------ | ------------------------------ |
| email              | string       | null: false, unique: true      |
| encrypted_password | string       | null: false                    |
| user_name          | string       | null: false                    |

### Association

- has_many : task

## tasks テーブル

| Column             | Type         | Options                        |
| ------------------ | ------------ | ------------------------------ |
| title              | string       | null: false                    |
| started_on         | date         | null: false                    |
| user               | references   | null: false, foreign_key: true |

### Association

- belongs_to : user
- has_one    : progress
- has_one    : repeat

## progress テーブル

| Column             | Type         | Options                        |
| ------------------ | ------------ | ------------------------------ |
| progress           | string       | null: false                    |
| task               | references   | null: false, foreign_key: true |

### Association

- belongs_to : task

## repeat テーブル

| Column             | Type         | Options                        |
| ------------------ | ------------ | ------------------------------ |
| count              | integer      | null: false                    |
| count_type         | string       | null: false                    |
| count_per          | integer      | null: false                    |
| interval           | integer      | null: false                    |
| task               | references   | null: false, foreign_key: true |

### Association

- belongs_to : task
