```zsh
> help name
> rudi

> help name --verbose
> Rodolfo Moi de Oliveira
```

```clj
(ns profile.core
    (:require
     [developer.core :refer [info]]))

(-> info (get :name))
; Rodolfo Mói de Oliveira
```
