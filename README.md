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

(->> dev/languages (map (comp keyword s/lower-case)) vec print)
; [:javascript :css :html :clojure :clojurescript :r :python]

(-> dev/contact print)
(comment "
  {:linkedin "https://www.linkedin.com/in/rodmoi/"
   :twitter "@rodmoi"}
   ")

(-> dev/projects :personal (project [:name :link]) print)
; #{{:name "pokestore"
;    :url "https://github.com/rodmoioliveira/pokestore"}
;   {:name "football-graphs"
;    :url "https://github.com/rodmoioliveira/football-graphs"}
;   {:name "soccer-knockout-standings"
;    :url "https://github.com/rodmoioliveira/soccer-knockout-standings"}}

(-> dev/projects :professional (project [:name :link]) vec (#(filter :proud? %)) print)
; ({:name "Qual é o maior jogador brasileiro da história?"
;   :url "https://interativos.globoesporte.globo.com/futebol/materia/melhor-jogador-brasileiro-oitavas"}
;  {:name "Maracanã 70 anos"
;   :url "https://interativos.globoesporte.globo.com/futebol/especial/maracana-70-anos"}
;  {:name "Simulador do Paulistão 2020"
;   :url "https://interativos.globoesporte.globo.com/futebol/campeonato-paulista/especial/simulador-do-paulista-2020"}
;  {:name "Ficou marcado na história"
;   :url "https://interativos.globoesporte.globo.com/futebol/times/flamengo/especial/ficou-marcado-na-historia"}
;  {:name "Estádio Olímpico Lujniki"
;   :url "https://interativos.globoesporte.globo.com/futebol/copa-do-mundo/especial/estadio-lujniki"}
;  {:name "Rota dos Convocados"
;   :url "https://interativos.globoesporte.globo.com/futebol/copa-do-mundo/especial/rota-dos-convocados"}
;  {:name "Toda a bola é quadrada - A geometria das bolas das copas"
;   :url "https://interativos.globoesporte.globo.com/futebol/copa-do-mundo/especial/toda-bola-e-quadrada"})
```
