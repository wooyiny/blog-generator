---
title: '{{ replace .File.ContentBaseName "-" " " | title }}'
date: {{ .Date }}
{{- /*  date: {{ .Date | time.Format "2006-01-02" }}  */ -}}
author: Yiny
draft: true
---
