```clojure

(ns profile.core
  (:require
   [clojure.string :as s]
   [clojure.set :refer [project]]

   [developer.core :as dev]))

; (-> dev/info (get :name) print)
"Rodolfo Mói de Oliveira"

; (-> dev/experience (get :current-job) print)
{:company "Globoesporte" :period {:begin 2018 :end nil} :role :developer}

; (->> dev/languages (map comp (keyword s/lower-case)) vec print)
[:javascript :css :html :clojure :clojurescript :r :python]

; (-> dev/projects :personnal (project [:name :link]) print)
#{{:name "pokestore"
   :url "https://github.com/rodmoioliveira/pokestore"}
  {:name "football-graphs"
   :url "https://github.com/rodmoioliveira/football-graphs"}
  {:name "soccer-knockout-standings"
   :url "https://github.com/rodmoioliveira/soccer-knockout-standings"}}

; (-> dev/projects :professional (project [:name :link]) vec (#(filter :proud?)) print)
({:name "Qual é o maior jogador brasileiro da história?"
  :url "https://interativos.globoesporte.globo.com/futebol/materia/melhor-jogador-brasileiro-oitavas"
  :company "Globoesporte"}
 {:name "Maracanã 70 anos"
  :url "https://interativos.globoesporte.globo.com/futebol/especial/maracana-70-anos"
  :company "Globoesporte"}
 {:name "Simulador do Paulistão 2020"
  :url "https://interativos.globoesporte.globo.com/futebol/campeonato-paulista/especial/simulador-do-paulista-2020"
  :company "Globoesporte"}
 {:name "Ficou marcado na história"
  :url "https://interativos.globoesporte.globo.com/futebol/times/flamengo/especial/ficou-marcado-na-historia"
  :company "Globoesporte"}
 {:name "Estádio Olímpico Lujniki"
  :url "https://interativos.globoesporte.globo.com/futebol/copa-do-mundo/especial/estadio-lujniki"
  :company "Globoesporte"}
 {:name "Rota dos Convocados"
  :url "https://interativos.globoesporte.globo.com/futebol/copa-do-mundo/especial/rota-dos-convocados"
  :company "Globoesporte"}
 {:name "Toda a bola é quadrada - A geometria das bolas das copas"
  :url "https://interativos.globoesporte.globo.com/futebol/copa-do-mundo/especial/toda-bola-e-quadrada"
  :company "Globoesporte"})
```
