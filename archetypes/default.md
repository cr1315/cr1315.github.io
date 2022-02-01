---
title: "{{ replace .Name "-" " " | title }}"
date: {{ .Date }}
draft: true


menu:
  sidebar:
    name: "{{ .File.Path }}"
    identifier: "{{ .File.Dir }}"
    weight: 30
---

