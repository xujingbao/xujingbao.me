---
title: Insufficient permission ... to repository
date: 2014-04-08
---
getting back an error while `git push`

insufficient permission for adding an object to repository database
<!-- more -->
```shell
$ ssh username@192.168.1.45

$ cd /git_repos

$ chmod -R g+ws *

$ chgrp -R git *

$ git config core.sharedRepository true

```


