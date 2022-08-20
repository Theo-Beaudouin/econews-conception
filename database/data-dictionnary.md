# Data Dictionnary

## User

| Field name     | Data type   | Field length | Constraint                                                 | *Description*                           |
| -------------- | ----------- | ------------ | ---------------------------------------------------------- | --------------------------------------- |
| `id`           | `INT`       | --           | `PRIMARY KEY` `UNSIGNED` `NOT NULL` `AUTO_INCREMENT`       | --                                      |
| `username`     | `VARCHAR`   | `64`         | `NOT NULL`                                                 | --                                      |
| `email`        | `VARCHAR`   | `64`         | `NOT NULL`                                                 | --                                      |
| `password`     | `VARCHAR`   | `20`         | `NOT NULL`                                                 | --                                      |
| `firstname`    | `VARCHAR`   | `32`         | `NOT NULL`                                                 | --                                      |
| `lastname`     | `VARCHAR`   | `32`         | `NOT NULL`                                                 | --                                      |
| `status`       | `ENUM`      | --           | `NOT NULL` `Default Active`                                                 | *(**Active**, **Deleted**, **Banned**)* |
| `is_confirmed` | `TINYINT`   | `1`          | `NOT NULL` `UNSIGNED` `DEFAULT 0`                          | *Account verified through email (**0** = Unverified, **1** = Verified)*        |
| `role`         | `ENUM`      | --           | `NOT NULL` `DEFAULT Member`                                                 | *(**Admin**, **Member**, **Author**)*   |
| created_at     | `TIMESTAMP` | --           | `NOT NULL` `DEFAULT CURRENT_TIMESTAMP`                     | --                                      |
| updated_at     | `TIMESTAMP` | --           | `NOT NULL` `CURRENT_TIMESTAMP ON UPDATE CURRENT_TIMESTAMP` | --                                      |

## Post

| Field name  | Data type    | Field length | Constraint                                                 | *Description*                                           |
| ----------- | ------------ | ------------ | ---------------------------------------------------------- | ------------------------------------------------------- |
| `id`        | `INT`        | --           | `PRIMARY KEY` `UNSIGNED` `NOT NULL` `AUTO_INCREMENT`       | --                                                      |
| `title`     | `VARCHAR`    | `255`        | `NOT NULL`                                                 | --                                                      |
| `content`   | `MEDIUMTEXT` | `1 000 000`  | `NOT NULL`                                                 | --                                                      |
| `status`    | `ENUM`       | --           | `NOT NULL` `DEFAULT Draft`                                 | *(**Published**, **Draft**, **Deleted**, **Privated**)* |
| `snippet`   | `TINYTEXT`   | `255`        | `NOT NULL`                                                 | *Preview of article's content or custom text*             |
| `thumbnail` | `VARCHAR`    | `256`        | --                                                         | *Picture pathname*                                      |
| created_at  | `TIMESTAMP`  | --           | `NOT NULL` `DEFAULT CURRENT_TIMESTAMP`                     | --                                                      |
| updated_at  | `TIMESTAMP`  | --           | `NOT NULL` `CURRENT_TIMESTAMP ON UPDATE CURRENT_TIMESTAMP` | --                                                      |

## Category

| Field name    | Data type   | Field length | Constraint                                                 | *Description*                              |
| ------------- | ----------- | ------------ | ---------------------------------------------------------- | ------------------------------------------ |
| `id`          | `INT`       | --           | `PRIMARY KEY` `UNSIGNED` `NOT NULL` `AUTO_INCREMENT`       | --                                         |
| `title`       | `VARCHAR`   | `64`         | `NOT NULL`                                                 | --                                         |
| `description` | `TINYTEXT`  | `255`        | `NOT NULL`                                                 | --                                         |
| `status`      | `ENUM`      | --           | `NOT NULL` `DEFAULT Draft`                                 | *(**Published**, **Draft**, **Privated**)* |
| created_at    | `TIMESTAMP` | --           | `NOT NULL` `DEFAULT CURRENT_TIMESTAMP`                     | --                                         |
| updated_at    | `TIMESTAMP` | --           | `NOT NULL` `CURRENT_TIMESTAMP ON UPDATE CURRENT_TIMESTAMP` | --                                         |

## SubCategory

| Field name    | Data type   | Field length | Constraint                                                 | *Description*                              |
| ------------- | ----------- | ------------ | ---------------------------------------------------------- | ------------------------------------------ |
| `id`          | `INT`       | --           | `PRIMARY KEY` `UNSIGNED` `NOT NULL` `AUTO_INCREMENT`       | --                                         |
| `title`       | `VARCHAR`   | `64`         | `NOT NULL`                                                 | --                                         |
| `description` | `TINYTEXT`  | `255`        | `NOT NULL`                                                 | --                                         |
| `status`      | `ENUM`      | --           | `NOT NULL` `DEFAULT Draft`                                 | *(**Published**, **Draft**, **Privated**)* |
| created_at    | `TIMESTAMP` | --           | `NOT NULL` `DEFAULT CURRENT_TIMESTAMP`                     | --                                         |
| updated_at    | `TIMESTAMP` | --           | `NOT NULL` `CURRENT_TIMESTAMP ON UPDATE CURRENT_TIMESTAMP` | --                                         |
