---
id: C-Sharp 12 Features
aliases: []
tags:
  - c-sharp
lang: c-sharp
---
[MSFT Learn](https://learn.microsoft.com/en-us/dotnet/csharp/whats-new/csharp-12)

Primary Constructors: 
Collection Expressions:  Spread Operator 

    int[] row0 = [1, 2, 3];
    int[] row1 = [4, 5, 6]; 
    int[] row2 = [7, 8, 9]; 
    int[] single = [.. row0, .. row1, .. row2];

ref readonly parameters: like IN keyword  
default lambda paramaters:  define default parameter for lambda function  
alias any type: not just named types but tuples, etc  
Inline arrays: like a struct  
experimental attribute: for a compiler warning
