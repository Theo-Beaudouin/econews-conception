# MPD

```SQL

DROP DATABASE IF EXISTS econews;
CREATE DATABASE econews;

-- User TABLE
DROP TABLE IF EXISTS econews.user;
CREATE TABLE econews.user (
    id int UNSIGNED PRIMARY KEY NOT NULL AUTO_INCREMENT,
    username varchar(64) NOT NULL,
    email varchar(64) NOT NULL,
    password varchar(64) NOT NULL,
    firstname varchar(64) NOT NULL,
    lastname varchar(64) NOT NULL,
    status enum('Active', 'Deleted', 'Banned') NOT NULL DEFAULT 'Active',
    is_confirmed tinyint(1) UNSIGNED NOT NULL DEFAULT 0,
    role enum('Admin', 'Member', 'Author') NOT NULL DEFAULT 'Member',
    created_at timestamp(6) NOT NULL DEFAULT CURRENT_TIMESTAMP,
    updated_at timestamp(6) NOT NULL DEFAULT CURRENT_TIMESTAMP ON UPDATE CURRENT_TIMESTAMP
) ENGINE=INNODB;

-- Category TABLE
DROP TABLE IF EXISTS econews.category;
CREATE TABLE econews.category (
    id int UNSIGNED PRIMARY KEY NOT NULL AUTO_INCREMENT,
    title varchar(64) NOT NULL,
    description varchar(255) NOT NULL,
    status enum('Published', 'Draft', 'Privated') NOT NULL DEFAULT 'Draft',
    created_at timestamp(6) NOT NULL DEFAULT CURRENT_TIMESTAMP,
    updated_at timestamp(6) NOT NULL DEFAULT CURRENT_TIMESTAMP ON UPDATE CURRENT_TIMESTAMP,
    user_id int UNSIGNED NOT NULL,
    FOREIGN KEY (user_id)
        REFERENCES user(id)
) ENGINE=INNODB;

-- INDEX CREATION FOR Category TABLE
CREATE INDEX cat_userid_ind ON econews.category (user_id);

-- SubCategory TABLE
DROP TABLE IF EXISTS econews.subCategory;
CREATE TABLE econews.subCategory (
    id int UNSIGNED PRIMARY KEY NOT NULL AUTO_INCREMENT,
    title varchar(64) NOT NULL,
    description varchar(255) NOT NULL,
    status enum('Published', 'Draft', 'Privated') NOT NULL DEFAULT 'Draft',
    created_at timestamp(6) NOT NULL DEFAULT CURRENT_TIMESTAMP,
    updated_at timestamp(6) NOT NULL DEFAULT CURRENT_TIMESTAMP ON UPDATE CURRENT_TIMESTAMP,
    category_id int UNSIGNED NOT NULL,
    user_id int UNSIGNED NOT NULL,
    FOREIGN KEY (category_id)
        REFERENCES category(id)
        ON DELETE CASCADE,

    FOREIGN KEY (user_id)
        REFERENCES user(id)
) ENGINE=INNODB;

-- INDEX CREATION FOR SubCategory TABLE
CREATE INDEX subcat_categoryid_ind ON econews.subCategory (category_id);
CREATE INDEX subcat_userid_ind ON econews.subCategory (user_id);

-- Post TABLE
DROP TABLE IF EXISTS econews.post;
CREATE TABLE econews.post (
    id int UNSIGNED PRIMARY KEY NOT NULL AUTO_INCREMENT,
    title varchar(255) NOT NULL,
    content mediumtext NOT NULL,
    status enum('Published', 'Draft', 'Deleted', 'Privated') NOT NULL DEFAULT 'Draft',
    snippet varchar(255) NOT NULL,
    thumbnail varchar(256),
    created_at timestamp(6) NOT NULL DEFAULT CURRENT_TIMESTAMP,
    updated_at timestamp(6) NOT NULL DEFAULT CURRENT_TIMESTAMP ON UPDATE CURRENT_TIMESTAMP,
    category_id int UNSIGNED NOT NULL,
    subcategory_id int UNSIGNED NOT NULL,
    user_id int UNSIGNED NOT NULL,
    FOREIGN KEY (category_id)
        REFERENCES category(id),

    FOREIGN KEY (subCategory_id)
        REFERENCES subCategory(id),

    FOREIGN KEY (user_id)
        REFERENCES user(id)
) ENGINE=INNODB;

-- INDEX CREATION FOR Post TABLE
CREATE INDEX post_categoryid_ind ON econews.post (category_id);
CREATE INDEX post_subcatid_ind ON econews.post (subcategory_id);
CREATE INDEX post_userid_ind ON econews.post (user_id);

```
