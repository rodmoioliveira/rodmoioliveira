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

(-> dev/projects :professional (project [:name :link]) vec (#(filter :proud?)) print)
; ({:name "Qual é o maior jogador brasileiro da história?"
;   :description "Chegou a hora de escolher o maior jogador brasileiro de todos os tempos. Pelé permanece absoluto? Alguém pode desbancar o Rei? Quem responde é você."
;   :url "https://interativos.globoesporte.globo.com/futebol/materia/melhor-jogador-brasileiro-oitavas"
;   :company "Globoesporte"}
;  {:name "Maracanã 70 anos"
;   :description "No aniversário do estádio, faremos uma viagem ao longo das décadas que transformaram o templo do futebol em uma verdadeira casa para o torcedor."
;   :url "https://interativos.globoesporte.globo.com/futebol/especial/maracana-70-anos"
;   :company "Globoesporte"}
;  {:name "Simulador do Paulistão 2020"
;   :description "Faça os cálculos para ver quem avança na competição, quem será adversário no mata-mata e quem será rebaixado. Simule os resultados dos próximos jogos, lembrando dos critérios de desempate em caso de igualdade por pontos: vitórias (V), saldo de gols (SG) e gols pró (GP)."
;   :url "https://interativos.globoesporte.globo.com/futebol/campeonato-paulista/especial/simulador-do-paulista-2020"
;   :company "Globoesporte"}
;  {:name "Ficou marcado na história"
;   :description "Nem o torcedor mais otimista imaginaria o desfecho da história do Brasileirão 2019. Com o passar dos meses, o batimento cardíaco do rubro-negro aumentou. Nos estádios, a história viva. Uma profusão de jogadas, gols, cantos, gritos e gestos que tomaram o país e estabeleceram novas marcas no futebol brasileiro."
;   :url "https://interativos.globoesporte.globo.com/futebol/times/flamengo/especial/ficou-marcado-na-historia"
;   :company "Globoesporte"}
;  {:name "Estádio Olímpico Lujniki"
;   :description "Este não é apenas mais um estádio da próxima Copa do Mundo. Principal palco da Olimpíada de 1980, sua história está repleta de memórias além do futebol. No cenário à sua volta, por baixo da recente cobertura e atrás das novas pilastras se revela a funcionalidade da arquitetura soviética, marcada por uma estética imponente que pode até contrastar com as novas tecnologias da arena, mas que continua sendo sinônimo da força e grandeza do antigo império."
;   :url "https://interativos.globoesporte.globo.com/futebol/copa-do-mundo/especial/estadio-lujniki"
;   :company "Globoesporte"}
;  {:name "Rota dos Convocados"
;   :description "O técnico Tite já escolheu os 23 jogadores que vão defender a Seleção na Copa do Mundo da Rússia, em junho. E o GloboEsporte.com mais uma vez apresenta a história da carreira de cada um dos escolhidos, mostrando por quais clubes passaram como profissionais e há quanto tempo defendem a camisa canarinho."
;   :url "https://interativos.globoesporte.globo.com/futebol/copa-do-mundo/especial/rota-dos-convocados"
;   :company "Globoesporte"}
;  {:name "Toda a bola é quadrada - A geometria das bolas das copas"
;   :description "O Globoesporte.com desmonta as bolas de todas as Copas e mostra como a tecnologia precisou voltar às origens para deixar a bola de futebol mais redonda e estável do que nunca para o Mundial de 2018."
;   :url "https://interativos.globoesporte.globo.com/futebol/copa-do-mundo/especial/toda-bola-e-quadrada"
;   :company "Globoesporte"})
```
