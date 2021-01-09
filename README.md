# README

This README would normally document whatever steps are necessary to get the
application up and running.

Things you may want to cover:

* Ruby version

* System dependencies

* Configuration

* Database creation

* Database initialization

* How to run the test suite

* Services (job queues, cache servers, search engines, etc.)

* Deployment instructions

* ...

# テーブル設計

## stores テーブル

| Column             | Type    | Options     |
| ------------------ | ------- | ----------- |
| email              | string  | null: false |
| encrypted_password | string  | null: false |
| store_name         | string  | null: false |

### Association

- has_many :staffs


## users テーブル

| Column             | Type    | Options     |
| ------------------ | ------- | ----------- |
| email              | string  | null: false |
| encrypted_password | string  | null: false |
| nickname           | string  | null: false |
| last_name          | string  | null: false |
| first_name         | string  | null: false |
| last_name_kana     | string  | null: false |
| first_name_kana    | string  | null: false |
| birth_date         | date    | null: false |

### Association

- has_many :staffs
- has_many :reservation_records


## staffs テーブル

| Column            | Type       | Options                        |
| ----------------- | ---------- | ------------------------------ |
| name              | string     | null: false                    |
| description       | text       | null: false                    |
| sex               | integer    | null: false                    |
| specialty_1_id    | integer    | null: false                    |
| specialty_2_id    | integer    | null: false                    |
| specialty_3_id    | integer    | null: false                    |
| store             | references | null: false, foreign_key: true |

- belongs_to :store
- has_many :reservation_record



## reservation_record テーブル

| Column          | Type       | Options                        |
| --------------- | ---------- | ------------------------------ |
| user            | references | null: false, foreign_key: true |
| staff           | references | null: false, foreign_key: true |

- belongs_to :staff
- belongs_to :user
- has_one :reservation_time

## reservation_time テーブル

| Column          | Type       | Options                        |
| --------------- | ---------- | ------------------------------ |
| month_id        | integer    | null: false                    |
| day_id          | integer    | null: false                    |
| time_id         | integer    | null: false                    |

- belongs_to :reservation_record