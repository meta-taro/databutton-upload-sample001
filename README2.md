# databuttonでブロックチェーンにテキストをアップしつつ、小遣いをもらう記述方法

```javascript
document.addEventListener("DOMContentLoaded", function(e) {
	databutton.build({
		data: ["0x6d0c", "テストなので短いテキスト"],
		button: {
			$el: "#button",
			$pay: {
				to: [{
					address: "支払うアドレス",
					value: サトシ
				}]
			},
			onPayment: function(msg) {
				console.log(msg)
				document.querySelector("a#tx").innerHTML = "View on B (" + msg.txid + ")"
				document.querySelector("a#tx").setAttribute("href", "https://b.bitdb.network#" + msg.txid)
			},
			onError: function(err) { console.log(err) }
		}
	})
})
```
