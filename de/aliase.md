---
layout: content
title: Aliase
prev: Konfiguration
next: Mathe
link_prev: /de/konfiguration.html
link_next: /en/mathe.html
---

Nu's konzept der Komposition von aneinandergereihten Operationen gibt dir eine Menge Kontrolle, aber dies kommt mit dem Preis viel zu tippen. Idealerweise würde man längere, selbstgebaute Ketten speichern können.

Dies ist, wo Aliase ins Spiel kommen.

Ein Alias erlaubt dir einen kurzen Namen für einen Block an Befehlen festzulegen. Wenn dieser Name als Befehl verwendet wird, wird der ganze Block ausgeführt.

Beispiel:

```
> alias ls-names [] { ls | select name }
> ls-names
────┬────────────────────
 #  │ name 
────┼────────────────────
  0 │ 404.html 
  1 │ CONTRIBUTING.md 
  2 │ Gemfile 
  3 │ Gemfile.lock 
  4 │ LICENSE 
```

## Parameter

Aliase können auch optionale Parameter annehmen, welche dem Block übergeben werden. Jeder Parameter wird eine neue Variable im Block.

```
> alias e [msg] { echo $msg }
> e "Hallo Welt!"
Hallo Welt!
```

Du kannst so viele Argumente im alias verwenden, wie du willst. Wenn der Nutzer keinen Wert für ein Argument gibt, evaluiert dieses zu nichts und wird gelöscht.

## Bestehen nach der Sitzung

Standardmäßig sind Aliase gültig, bis die Sitzung vorbei ist. Dies kann sinnvoll sein für temporäre Helferfunktionen oder um neue Aliase zu testen, aber um Aliase effektiv nutzen zu können, müssen sie gespeichert werden können. Dazu kannst du den `alias` befehl mit der `--save` flag (oder der Abkürzung `-s`) aufrufen. Ein Beispiel:

```
alias e --save [msg] { echo $msg }
```

Aliase werden in der `startup` konfiguration gespeichert, welche du mit `config get startup` einsehen kannst. Wenn du eine Fehlermeldung bekommst, existiert die `startup` konfiguration noch nicht.

Weiters kannst du aliase direkt in der config.toml Datei ändern, mit `vi` zum Beispiel:

```
config path | vi $it
```
