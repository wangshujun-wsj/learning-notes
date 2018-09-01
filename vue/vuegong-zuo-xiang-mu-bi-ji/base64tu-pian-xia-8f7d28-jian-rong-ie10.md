[参考](https://blog.csdn.net/Vir_czz/article/details/59580925)

```
//判断浏览器类型
function isBrowser() {
  var userAgent = navigator.userAgent; //取得浏览器的userAgent字符串
  var isOpera = userAgent.indexOf("OPR") > -1;
  if (isOpera) {
    return "Opera"
  } //判断是否Opera浏览器 OPR/43.0.2442.991

  //if (userAgent.indexOf("compatible") > -1 && userAgent.indexOf("MSIE") > -1 && !isOpera) { return "IE"; }; //判断是否IE浏览器

  if (userAgent.indexOf("Firefox") > -1) {
    return "FF";
  } //判断是否Firefox浏览器  Firefox/51.0
  if (userAgent.indexOf("Trident") > -1) {
    return "IE";
  } //判断是否IE浏览器  Trident/7.0; rv:11.0
  if (userAgent.indexOf("Edge") > -1) {
    return "Edge";
  } //判断是否Edge浏览器  Edge/14.14393
  if (userAgent.indexOf("Chrome") > -1) {
    return "Chrome";
  }// Chrome/56.0.2924.87
  if (userAgent.indexOf("Safari") > -1) {
    return "Safari";
  } //判断是否Safari浏览器 AppleWebKit/534.57.2 Version/5.1.7 Safari/534.57.
}

const downloadBase = {
  // 下载base64的二维码图片(谷歌 火狐)
  ffDownload: function(fileName, content) {
    const a = document.createElement('a');
    const event = new MouseEvent('click');
    // 下载图名字
    a.download = fileName;
    //url
    a.href = content;
    //合成函数，执行下载
    a.dispatchEvent(event);
  },
  // 下载base64的二维码图片(ie11)
  ieDownload: function (fileName,content) {
    let blob = this.base64ToBlob(content); //new Blob([content]);

    window.navigator.msSaveBlob(blob, fileName)
  },
  // 下载base64的二维码图片 (谷歌edge)
  downloadFile: function(fileName, content) {

    let aLink = document.createElement('a');
    let blob = this.base64ToBlob(content); //new Blob([content]);

    let evt = document.createEvent("HTMLEvents");
    evt.initEvent("click", true, true);
    aLink.download = fileName;
    aLink.href = URL.createObjectURL(blob);

    // aLink.dispatchEvent(evt);
    aLink.click()
  },
  //base64转blob
  base64ToBlob: function(code) {
    let parts = code.split(';base64,');
    let contentType = parts[0].split(':')[1];
    let raw = window.atob(parts[1]);
    let rawLength = raw.length;

    let uInt8Array = new Uint8Array(rawLength);

    for (let i = 0; i < rawLength; ++i) {
      uInt8Array[i] = raw.charCodeAt(i);
    }
    return new Blob([uInt8Array], {type: contentType});
  }
};
```

使用

```
	// isBrowser 和 downloadBase 是通用js文件里定义的
	download() {
        var oQrcode = document.querySelector('#qrcode img');
        // src 存放的是base64的图片
        var url = oQrcode.src;
        const name = "企业 二维码.png";
        const browser = isBrowser();
        if (browser === "IE") {
          downloadBase.ieDownload(name, url)
        } else if (browser === "FF") {
          downloadBase.ffDownload(name, url);
        } else {
          downloadBase.downloadFile(name, url);
        }
      },
```