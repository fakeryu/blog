---
slug: nicefuncs
title: Nice-Funcs
authors:
  name: BergYu
  # title: how to judge it
tags: [funcs]
---

1.  judge datatype by toString:

        function(val){
        	return Object.prototype.toString.call([]).slice(8,-1).toLowerCase();
        }

2.  deepClone

          function shallowCopy(obj) {
              if (typeof obj !== 'object') return

              let newObj = obj instanceof Array ? [] : {}
                for (let key in obj) {
              if (obj.hasOwnProperty(key)) {
                newObj[key] = obj[key]
              }
            }
            return newObj
          }
3. picture lazy-loading

        let imgList = [...document.querySelectorAll('img')]
        let length = imgList.length

        const imgLazyLoad = (function() {
        let count = 0

        return function() {
        let deleteIndexList = []

        imgList.forEach((img, index) => {
            let rect = img.getBoundingClientRect()
            if (rect.top < window.innerHeight) {
                img.src = img.dataset.src
                deleteIndexList.push(index)
                count++
                if (count === length) {
                    document.removeEventListener('scroll', imgLazyLoad)
                }
            }
        })
        imgList = imgList.filter((img, index) => !deleteIndexList.includes(index))
          }
        })()