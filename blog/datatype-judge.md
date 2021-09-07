---
slug: datatype
title: Datatype-Judge
authors:
  name: Berg
  title: how to judge it
tags: [funcs]
---

1.  judge datatype by toString:

        function(val){
        			return Object.prototype.toString.call([]).slice(8,-1).toLowerCase();
        		}
