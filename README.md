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
"Rodolfo Mói de Oliveira"

(-> info (get :current-job))
{:company "Globoesporte" :period "2010-now" :role :developer}
```
