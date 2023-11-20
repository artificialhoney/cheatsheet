---
layout: default
title: php
parent: Cheatsheet
nav_order: 2
---

# php

## [How to include() all PHP files from a directory](https://stackoverflow.com/questions/599670/how-to-include-all-php-files-from-a-directory)

```php
foreach (glob("classes/*.php") as $filename)
{
    include $filename;
}
```