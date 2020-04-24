---
chapter: SQL
title: Transactions
---

To use a transaction simply wrap an operation via `Relation#transaction` method:

``` ruby
# rollback happens when any error is raised
users.transaction do |t|
  users.command(:create).call(name: "jane")
end

# manual rollback
users.transaction do |t|
  users.command(:create).call(name: "Jane")
  t.rollback!
end
```

You can also use `Repository#transaction` in the same fashion.

It is also equivalent to use the connection gateway:
``` ruby
rom_container.gateways[:default].transaction do |t|
  # Your transaction...
end
```

## Learn more

* [api::rom-sql::SQL/Relation](#transaction)
