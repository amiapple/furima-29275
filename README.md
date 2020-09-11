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

## users テーブル

| Column   | Type   | Options     |
| -------- | ------ | ----------- |
| user     | string | null: false |
| email    | string | null: false |
| password | string | null: false |
| first_name   | string | null: false |
| family_name    | string | null: false |
| first_name_kana   | string | null: false |
| family_name_kana   | string | null: false |
| birthday   | data | null: false |

### Association

- has_many :products
- has_many :comments

## products テーブル

| Column       | Type   | Options     |
| ------------ | ------ | ----------- |
| name         | string | null: false |
| price        | integer | null: false |
| category     | integer | null: false |
| bland        | integer | null: false |
| introduction | text | null: false |
| condition    | integer | null: false |
| postage      | integer | null: false,foreign_key:true |
| shipping_area| integer | null: false,foreign_key:true |
| preparation_day | integer | null: false,foreign_key:true |

### Association

- has_many :comments
- has_many :product_image
- belongs_to :user

## comments テーブル

| Column   | Type   | Options     |
| -------- | ------ | ----------- |
| comment   | string | null: false |
| user    | string | null: false |
| item    | string | null: false |

### Association

- belongs_to :user
- belongs_to :product

## product_purchases テーブル

| Column   | Type   | Options     |
| -------- | ------ | ----------- |
| user_id  | integer | null: false,foreign_key:true |
| item_id  | integer | null: false,foreign_key:true |

### Association

- belongs_to :user
- belongs_to :product

## sending_destinations テーブル

| Column   | Type   | Options     |
| -------- | ------ | ----------- |
| user | references | null: false,foreign_key:true |
| destination_first_name | string | null: false |
| destination_family_name  | string | null: false |
| destination_first_name_kana | string | null: false |
| destination_family_name_kana | string | null: false |
| post_code | integer | null: false |
| prefecture_code | integer | null: false |
| city | string | null: false |
| building_name | string | null: false |
| phone_number | string | null: false |


### Association

- belongs_to :product