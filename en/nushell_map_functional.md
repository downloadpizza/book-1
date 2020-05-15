---
layout: content
title: NuShell map from functional languages
prev: Imperative map 
next: Operator map
link_prev: /en/nushell_map_imperative.html
link_next: /en/nushell_operator_map.html 
---

The idea behind this table is to help you understand how NuShell built-ins and plug-ins relate to functional languages. We've tried to produce a map of all the nushell commands and what their equivalents are in other languages. Contributions are welcome.

Note: this table assumes Nushell 0.13.1 or later.


| NuShell                | Clojure                       | Tablecloth (Ocaml / Elm)                             | Haskell                                    |
| ---------------------- | ----------------------------- | ---------------------------------------------------- | ------------------------------------------ | ----------------------------------------------- |
| alias                  |                               |                                                      |                                            |                                                 |
| append                 | conj                          | append                                               | (++)                                       |                                                 |
| args                   |                               |                                                      |                                            |                                                 |
| autoview               |                               |                                                      |                                            |                                                 |
| average(`*`)           |                               |                                                      |                                            |                                                 |
| binaryview(`*`)        | Integer/toHexString           |                                                      | showHex                                    |                                                 |
| calc, = math           | math operators                |                                                      |                                            |                                                 |
| cd                     |                               |                                                      |                                            |                                                 |
| clear                  |                               |                                                      |                                            |                                                 |
| clip                   |                               |                                                      |                                            |                                                 |
| compact                |                               |                                                      |                                            |                                                 |
| config                 |                               |                                                      |                                            |                                                 |
| count                  | count                         | length                                               | length                                     |                                                 |
| cp                     |                               |                                                      |                                            |                                                 |
| date                   | java.time.LocalDate/now       |                                                      | Get-Date                                   |                                                 |
| debug                  |                               |                                                      |                                            |                                                 |
| = dec                  | dec                           |                                                      | pred                                       |                                                 |
| default                |                               |                                                      |                                            |                                                 |
| drop                   |                               |                                                      |                                            |                                                 |
| du                     |                               |                                                      |                                            |                                                 |
| each                   | map                           | map                                                  | map                                        |                                                 |
| echo                   | println                       |                                                      | putStrLn, print                            |                                                 |
| enter                  |                               |                                                      |                                            |                                                 |
| evaluate_by            |                               |                                                      |                                            |                                                 |
| exit                   | System/exit                   |                                                      |                                            |                                                 |
| fetch(`*`)             |                               |                                                      |                                            |                                                 |
| first                  | first                         | head                                                 | head                                       |                                                 |
| format                 | format                        |                                                      | Text.Printf.printf                         |                                                 |
| from bson              |                               |                                                      |                                            |                                                 |
| from csv               |                               |                                                      |                                            |                                                 |
| from eml               |                               |                                                      |                                            |                                                 |
| from ics               |                               |                                                      |                                            |                                                 |
| from ini               |                               |                                                      |                                            |                                                 |
| from json              |                               |                                                      |                                            |                                                 |
| from ods               |                               |                                                      |                                            |                                                 |
| from sqlite            |                               |                                                      |                                            |                                                 |
| from ssv               |                               |                                                      |                                            |                                                 |
| from toml              |                               |                                                      |                                            |                                                 |
| from tsv               |                               |                                                      |                                            |                                                 |
| from url               |                               |                                                      |                                            |                                                 |
| from vcf               |                               |                                                      |                                            |                                                 |
| from xlsx              |                               |                                                      |                                            |                                                 |
| from xml               |                               |                                                      |                                            |                                                 |
| from yaml              |                               |                                                      |                                            |                                                 |
| get                    |                               |                                                      |                                            |                                                 |
| grep                   | filter                        |                                                      | filter                                     |                                                 |
| group_by               | group-by                      |                                                      |                                            |                                                 |
| headers                |                               |                                                      |                                            |                                                 |
| help                   | doc                           |                                                      |                                            |                                                 |
| histogram              |                               |                                                      |                                            |                                                 |
| history                |                               |                                                      |                                            |                                                 |
| inc(`*`)               | inc                           |                                                      | succ                                       |                                                 |
| insert                 |                               |                                                      |                                            |                                                 |
| is_empty               | empty?                        |                                                      |                                            |                                                 |
| keep                   | take, drop-last, pop          | take, init                                           | take, init                                 |                                                 |
| keep_until             |                               |                                                      |                                            |                                                 |
| keep_while             | take-while                    | takeWhile                                            |                                            |                                                 |
| kill                   |                               |                                                      |                                            |                                                 |
| last                   | last, peek                    | last                                                 | last                                       |                                                 |
| lines                  |                               |                                                      | lines, words, split-with                   |                                                 |
| ls                     |                               |                                                      |                                            |                                                 |
| map_max_by             |                               |                                                      |                                            |                                                 |
| match(`*`)             |                               |                                                      |                                            |                                                 |
| merge                  |                               |                                                      |                                            |                                                 |
| mkdir                  |                               |                                                      |                                            |                                                 |
| mv                     |                               |                                                      |                                            |                                                 |
| next                   |                               |                                                      |                                            |                                                 |
| nth                    | nth                           |                                                      |                                            |                                                 |
| open                   | with-open                     |                                                      |                                            |                                                 |
| parse                  |                               |                                                      |                                            |                                                 |
| pivot                  | (apply mapv vector matrix)    |                                                      | transpose                                  |                                                 |
| post(`*`)              |                               |                                                      |                                            |                                                 |
| prepend                | cons                          | cons, ::                                             | ::                                         |                                                 |
| prev                   |                               |                                                      |                                            |                                                 |
| ps(`*`)                |                               |                                                      |                                            |                                                 |
| pwd                    |                               |                                                      |                                            |                                                 |
| range                  | range                         | range                                                | 1..10, 'a'..'f'                            |                                                 |
| reduce_by              |                               |                                                      |                                            |                                                 |
| reject                 |                               |                                                      |                                            |                                                 |
| rename                 |                               |                                                      |                                            |                                                 |
| reverse                |                               |                                                      |                                            |                                                 |
| rm                     |                               |                                                      |                                            |                                                 |
| save                   |                               |                                                      |                                            |                                                 |
| select(`***`)          | select-keys                   |                                                      |                                            |                                                 |
| shells                 |                               |                                                      |                                            |                                                 |
| shuffle                | shuffle                       |                                                      |                                            |                                                 |
| size                   | count                         |                                                      |                                            |                                                 |
| skip                   | rest                          | tail                                                 | tail                                       |                                                 |
| skip_until             |                               |                                                      |                                            |                                                 |
| skip_while             |                               |                                                      |                                            |                                                 |
| sort-by                | sort, sort-by                 |                                                      |                                            |                                                 |
| split_by               | split                         | split, words, lines                                  | split, words, lines                        |                                                 |
| split_column           |                               |                                                      |                                            |                                                 |
| split_row              |                               |                                                      |                                            |                                                 |
| str(`*`)               | clojure.string functions      |                                                      |                                            |                                                 |
| sum                    |                               |                                                      |                                            |                                                 |
| sys(`*`)               |                               |                                                      |                                            |                                                 |
| table                  |                               |                                                      |                                            |                                                 |
| tags                   |                               |                                                      |                                            |                                                 |
| textview(`*`)          |                               |                                                      |                                            |                                                 |
| tree(`*`)              |                               |                                                      |                                            |                                                 |
| to bson                |                               |                                                      |                                            |                                                 |
| to csv                 |                               |                                                      |                                            |                                                 |
| to html                |                               |                                                      |                                            |                                                 |
| to json                |                               |                                                      |                                            |                                                 |
| to md                  |                               |                                                      |                                            |                                                 |
| to sqlite              |                               |                                                      |                                            |                                                 |
| to toml                |                               |                                                      |                                            |                                                 |
| to tsv                 |                               |                                                      |                                            |                                                 |
| to url                 |                               |                                                      |                                            |                                                 |
| to yaml                |                               |                                                      |                                            |                                                 |
| touch                  |                               |                                                      |                                            |                                                 |
| trim                   |                               |                                                      |                                            |                                                 |
| uniq                   |                               |                                                      |                                            |                                                 |
| update(`**`)           |                               |                                                      |                                            |                                                 |
| version                |                               |                                                      |                                            |                                                 |
| with_env               |                               |                                                      |                                            |                                                 |
| what                   |                               |                                                      |                                            |                                                 |
| where                  | filter                        |                                                      | filter                                     |                                                 |
| which                  |                               |                                                      |                                            |                                                 |
| wrap                   |                               |                                                      |                                            |                                                 |

* `*` - these commands are part of the standard plugins
* `**` - renamed from `edit` to `update` in 0.13.1
* `***` - renamed from `pick` to `select` in 0.13.1
