# ASCIIImage
<h1><img class="alignnone  wp-image-99" src="https://catmaoblog.files.wordpress.com/2016/10/6lqz4de.png" alt="Icon made by Freepik from www.flaticon.com" width="40" height="40" /> <a href="https://catmao1230.github.io/ASCIIImage/" target="_blank">點我前往</a></h1>
<h1><img class="alignnone  wp-image-99" src="https://catmaoblog.files.wordpress.com/2016/10/6lqz4de.png" alt="Icon made by Freepik from www.flaticon.com" width="40" height="40" /> <a href="https://catmaoblog.wordpress.com/2016/10/10/ascii-image/" target="_blank">WordPress</a></h1>
<h1><img class="alignnone  wp-image-41" src="https://catmaoblog.files.wordpress.com/2016/10/3h9rzur.png" alt="Icon made by Popcorns Arts from www.flaticon.com" width="40" height="40" /> ASCII Image介紹</h1>
又名「文字圖」、「字元畫」、「文字畫」，用文字來顯示出圖片的樣子。
<h1><img class="alignnone  wp-image-43" src="https://catmaoblog.files.wordpress.com/2016/10/ril6i6c.png" alt="ril6i6c" width="40" height="40" /> 程式碼</h1>
<ol>
	<li>將 canvas 大小改為圖片大小，並將圖像片在 canvas 上</li>
	<li>若圖片大於 100px 則縮小成 0.1 倍，如果不縮會很 LAG （其實不應該硬性規定，應該隨視窗大小調整縮放比例，不過我目前只這樣寫，可以自己調整）</li>
	<li>利用 getImageData 得到像素，並將這些像素的 data 放進字串 str， imgData 裡存了每個像素的 RGBA ，所以可以藉由迴圈讀取圖片的像素資料加以處理。
<pre><code>var canvas = document.getElementById("canvas");
var cxt    = canvas.getContext("2d");
var img    = document.getElementById("img");
cxt.drawImage(img,0,0);
var imgData = cxt.getImageData(0, 0, canvas.width, canvas.height);
var R, G, B, A;
// 每點像素都是 4byte ，存取了其像素的 R、G、B、A
</code><code>for (var i = 0; i < imgData.data.length; i += 4)
{
     R = imgData.data[i];
     G = imgData.data[i+1];
     B = imgData.data[i+2];
     A = imgData.data[i+3];
}</code></pre>
</li>
	<li>將 str 放進 textarea 裡並顯示在視窗內</li>
</ol>
值得一提的是：我原本是直接改變文字框的內容（ textarea.innerHTML ），但是這樣跑起來效率很差，後來改成先放在字串 str 內，最後再放進 textarea ，效能就提升了許多。
<h1></h1>
<h1><img class="alignnone  wp-image-42" src="https://catmaoblog.files.wordpress.com/2016/10/tpodion.png" alt="tpodion" width="40" height="40" /> 參考資料</h1>
<ul class="alt">
	<li><a href="https://zh.wikipedia.org/wiki/ASCII%E8%89%BA%E6%9C%AF" target="_blank">ASCII藝術 / 維基百科</a></li>
	<li><a href="http://www.w3school.com.cn/tags/canvas_getimagedata.asp" target="_blank">HTML5 canvas getImageData() 方法 / W3School</a></li>
</ul>
