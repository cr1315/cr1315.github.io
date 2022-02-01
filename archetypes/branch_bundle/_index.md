---
title: "Posts"
menu:
  sidebar:
    name: "{{ .File.Dir }}"
    identifier: "{{ .File.Path }}"
    weight: {{ substr .File.BaseFileName 0 3 }}
---  

