```zsh
> help name
> rudi

> help name --verbose
> Rodolfo Moi de Oliveira
```

```clojure

(ns profile.core
  (:require
   [clojure.string :as s]
   [developer.core :as dev]))

(-> dev/info (get :name) print)
; "Rodolfo Mói de Oliveira"

(-> dev/experience (get :current-job) print)
; {:company "Globoesporte" :period {:begin 2018 :end nil} :role :developer}

(->> dev/languages (map comp(keyword s/lower-case)) vec print)
; [:javascript :css :html :clojure :clojurescript :r :python]
```
