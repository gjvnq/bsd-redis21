# Database

## Long Lived Keys

| Name                  | Type   | Format        | Description                                          |
| --------------------- | ------ | ------------- | ---------------------------------------------------- |
| `all_users`           | SET    | UUIDs         | List of all existing users.                          |
| `all_seats`           | SET    | UUIDs         | List of all existing seats.                          |
| `email2user`          | HSET   | STRING:STRING | Associates each email address to an user UUID.       |

## Medium Lived Keys

| Name                   | Type   | Format        | Description                                                                 |
| ---------------------- | ------ | ------------- | --------------------------------------------------------------------------- |
| `pairs_to_calc_queue`  | ZSET   | UUID pair     | Queue of (slot, entity) pairs whose match value that need to be calculated. |
