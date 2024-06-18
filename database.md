https://shopify.engineering/building-resilient-payment-systems
"In one high-throughput system at Shopify we’ve seen a 50 percent decrease in INSERT statement duration by switching from UUIDv4 to ULID for idempotency keys."

with MySQL InnoDB backend a table itself is a primary key B-Tree index
https://www.cybertec-postgresql.com/en/unexpected-downsides-of-uuid-keys-in-postgresql/
