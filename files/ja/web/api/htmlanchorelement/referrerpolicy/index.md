---
title: HTMLAnchorElement.referrerPolicy
slug: Web/API/HTMLAnchorElement/referrerPolicy
---

{{APIRef}}

**`HTMLAnchorElement.referrerPolicy`** プロパティは、リソースの取得時に送信されるリファラーを定義する {{HTMLElement("a")}} 要素の HTML [`referrerpolicy`](/ja/docs/Web/HTML/Element/a#referrerpolicy) 属性を反映します。

## 値

文字列で、以下のうちの一つです。

- `no-referrer`
  - : {{HTTPHeader("Referer")}} ヘッダーは完全に省略されます。リクエストと共に送信されるリファラー情報はありません。
- `no-referrer-when-downgrade`
  - : プロトコルのセキュリティレベルが変わらない場合（例: HTTP→HTTP、HTTPS→HTTPS）にはリファラーとして URL を送信し、セキュリティレベルの低い宛先（例: HTTPS→HTTP）には送信しません。
- `origin`
  - : どのような場合でも、この文書のオリジンだけをリファラーとして送信します。
    文書 `https://example.com/page.html` はリファラーとして `https://example.com/` を送ります。
- `origin-when-cross-origin`
  - : 同一オリジンリクエストを行う場合は完全な URL を送信し、それ以外の場合は文書のオリジンのみを送信します。
- `same-origin`
  - : リファラーは[同一サイトオリジン](/ja/docs/Web/Security/Same-origin_policy)には送信されますが、オリジン間リクエストではリファラー情報が送信されません。
- `strict-origin`
  - : プロトコルのセキュリティレベルが変わらない場合（例: HTTPS→HTTPS）だけ、文書のオリジンをリファラーとして送信し、セキュリティレベルの低い宛先（例: HTTPS→HTTP）には送信しないようにします。
- `strict-origin-when-cross-origin` (default)
  - : これは、ポリシーが指定されていない場合のユーザーエージェントの既定の動作です。同一オリジンリクエストを行う場合は完全な URL を送信し、プロトコルのセキュリティレベルが変わらない場合はオリジンのみを送信し（例: HTTPS→HTTPS）、セキュリティレベルの低い宛先にはヘッダーを送信しません（例: HTTPS→HTTP）。
- `unsafe-url`
  - : 同一オリジンまたはオリジン間リクエストを実行するときに、完全な URL を送信します。このポリシーは、 TLS で保護されたリソースから安全でないオリジンへのオリジンとパスを漏洩します。
    この設定の影響を慎重に検討してください。

## 例

```js
var elt = document.createElement("a");
var linkText = document.createTextNode("My link");
elt.appendChild(linkText);
elt.href = "https://developer.mozilla.org/en-US/";
elt.referrerPolicy = "no-referrer";

var div = document.getElementById("divAround");
div.appendChild(elt); // クリックしても、リンクはリファラーのヘッダーを送信しません。
```

## 仕様書

{{Specifications}}

## ブラウザーの互換性

{{Compat}}

## 関連情報

- {{domxref("HTMLImageElement.referrerPolicy")}},
  {{domxref("HTMLAreaElement.referrerPolicy")}},
  {{domxref("HTMLIFrameElement.referrerPolicy")}}
