---
title: 原生js下载pdf链接文件而不是打开预览的解决方案
date: 2020-05-26 18:03:13
tags:
 - pdf
 - js 下载 pdf 链接文件
categories:
 - javascript
---



## 点击 pdf 链接的时候直接下载 pdf 文件到本地, 而非打开新的页面进行预览


```javascript


// 通过 blob 下载
function saveAs(blob, filename) {
  const URL = window.URL || window.webkitURL
  const type = blob.type
  const force_saveable_type = 'application/octet-stream'
  if (type && type !== force_saveable_type) { // 强制下载，而非在浏览器中打开
    const slice = blob.slice || blob.webkitSlice || blob.mozSlice
    blob = slice.call(blob, 0, blob.size, force_saveable_type)
  }
  const url = URL.createObjectURL(blob)
  const save_link = document.createElementNS('http://www.w3.org/1999/xhtml', 'a')
  save_link.href = url
  save_link.download = filename

  const event = new MouseEvent('click', {
    bubbles: true,
    cancelable: true,
    view: window
  })
  save_link.dispatchEvent(event)
  URL.revokeObjectURL(url)
}


// 根据 file url 获取 blob
function fetchPdfBlob(fileUrl, fileName) {
  const oReq = new XMLHttpRequest()
  oReq.open('GET', fileUrl, true)
  oReq.responseType = 'blob'
  oReq.onload = function() {
    const fileBlob = new Blob([oReq.response], {
      type: 'application/pdf'
    })
    saveAs(fileBlob, fileName)
  }
  oReq.send()
}



// 调用
button.onclick = function () {
  fetchPdfBlob('https://xxxx.pdf')
}


```
