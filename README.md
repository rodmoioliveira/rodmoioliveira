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
   [clojure.set :refer [project]]

   [developer.core :as dev]))

(-> dev/info (get :name) print)
; "Rodolfo Mói de Oliveira"

(-> dev/experience (get :current-job) print)
; {:company "Globoesporte" :period {:begin 2018 :end nil} :role :developer}

(->> dev/languages (map comp(keyword s/lower-case)) vec print)
; [:javascript :css :html :clojure :clojurescript :r :python]

(-> dev/projects :personnal (project [:name :link]) print)
; #{{:name "pokestore" :url "https://github.com/rodmoioliveira/pokestore"}
;   {:name "football-graphs" :url "https://github.com/rodmoioliveira/football-graphs"}
;   {:name "soccer-knockout-standings" :url "https://github.com/rodmoioliveira/soccer-knockout-standings"}}
```
