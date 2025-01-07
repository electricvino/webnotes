---
id: 1735959925-THTQ
aliases:
  - JQ
tags:
  - cli-tools
---

# JQ

Utility for querying JSON.

## Examples
From [[https://www.youtube.com/watch?v=n8sOmEe2SDg&t=496s|YT]]


  // Parse out with space; compact with -c
  jq < filename

  // get one field without quotes
  jq -r .PropName < filename

  // create new objects
  jq '{id: .id, logs: .logs}' < filename

  // filter empty properties; also use has(logs)
  jq 'select(.logs | length > 0)' < filename

  // add values to filter
  jq 'select(.values.a + .values.b > 1)' < filename

  // filter with conditional logs
  jq 'select(.errors | length > 0 AND any(.[]; contains("wife")))' < filename

The following commands are done inside [[dev tools/neovim]]
  :(range selector)!jq   //whitespaces json line selected in visual mode. 

  :%!jq  //whitespaces the entire file

All previous JQ statements can be run in Neovim/VIM using :%!jq commands
