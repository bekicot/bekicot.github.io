---
layout: post
title: Sorting line of codes in vim
category: snacks
---

I have this hash

```ruby
  ATTRIBUTE_TYPES = {
    id: Field::Number.with_options(searchable: true),
    created_at: Field::DateTime,
    updated_at: Field::DateTime,
    address_line_one: Field::String,
    address_line_two: Field::String,
    address_city: Field::String,
    address_state: Field::String,
    address_zip: Field::String,
    customer: Field::BelongsTo,
    line_items: Field::HasMany,
    total_price: Field::Number.with_options(prefix: "$", decimals: 2),
    shipped_at: Field::DateTime,
    payments: Field::HasMany,
  }
```

[Taken From OrderDashbard](https://github.com/thoughtbot/administrate/blob/29d63ee/spec/example_app/app/dashboards/order_dashboard.rb)

I want to sort it so that it will transform into:

```ruby
  ATTRIBUTE_TYPES = {
    address_city: Field::String,
    address_line_one: Field::String,
    address_line_two: Field::String,
    address_state: Field::String,
    address_zip: Field::String,
    created_at: Field::DateTime,
    customer: Field::BelongsTo,
    id: Field::Number.with_options(searchable: true),
    line_items: Field::HasMany,
    payments: Field::HasMany,
    shipped_at: Field::DateTime,
    total_price: Field::Number.with_options(prefix: "$", decimals: 2),
    updated_at: Field::DateTime,
  }
```

To sort it, select the lines inside curly braces with:

```vi
vi{
```

and then type

```vi
:sort
```

note that upon typing `:` you will have `:'<,'>`. So the completed command will
be `:'<,'>sort`.

