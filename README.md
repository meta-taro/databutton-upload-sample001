# moneybutton決済でブロックチェーンにファイルをアップする

```html:test.html
<html>
<head>
<style>
input#file { display: block; padding: 10px; background: whitesmoke; width: 100%; margin: 10px 0; }
a#tx { display: block; padding: 10px; margin: 10px 0; color: red; font-size: 12px; font-family: Menlo, monaco, Courier; }
</style>
<script src="//www.moneybutton.com/moneybutton.js"></script>
<script src='//unpkg.com/databutton@0.0.4/index.js'></script>

<?php
/**
 * アップされたファイルをmbで支払わせ、BCに保存する
**/
?>

<script>
document.addEventListener("DOMContentLoaded", function(e) {
	databutton.build({
		file: {
			$el: "#file",
			data: [
				 "0x6d02"
				,databutton.file
				,databutton.type
				,'binary'
				,databutton.name
			],
		},
		button: {
			$el: "#button",
			onPayment: function(msg) {
				console.log(msg)
				document.querySelector("a#tx").innerHTML = "View on B (" + msg.txid + ")"
				document.querySelector("a#tx").setAttribute("href", "https://b.bitdb.network#" + msg.txid)
			},
			onError: function(err) { console.log(err) }
		}
	})
})
</script>
</head>
<body>
	<?php /*** moneybuttonアカウントがあればブロックチェーンにアップできる ***/ ?>
	<input type='file' id='file'>
	<a target='_blank' href='#' id='tx'></a>
	<div id='button'></div>
	<?php /*** moneybuttonアカウントがあればブロックチェーンにアップできる ***/ ?>
</body>
</html>
```
