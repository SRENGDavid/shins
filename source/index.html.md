---
title: Electre API
language_tabs:
  - shell: Shell
  - http: HTTP
  - javascript: JavaScript
  - javascript--nodejs: Node.JS
  - ruby: Ruby
  - python: Python
  - java: Java
  - go: Go
toc_footers: []
includes: []
search: true
highlight_theme: darkula
headingLevel: 2

---

<h1 id="electre-api">Electre API v1.0.0</h1>

> Scroll down for code samples, example requests and responses. Select a language for code samples from the tabs above or the mobile navigation menu.

Electre API

Email: <a href="mailto:api@electre.com">Electre API Team</a> Web: <a href="https://www.electre.com">Electre API Team</a> 

<h1 id="electre-api-notices">notices</h1>

## get__notices

> Code samples

```shell
# You can also use wget
curl -X GET /notices \
  -H 'Accept: */*'

```

```http
GET /notices HTTP/1.1

Accept: */*

```

```javascript
var headers = {
  'Accept':'*/*'

};

$.ajax({
  url: '/notices',
  method: 'get',

  headers: headers,
  success: function(data) {
    console.log(JSON.stringify(data));
  }
})

```

```javascript--nodejs
const fetch = require('node-fetch');

const headers = {
  'Accept':'*/*'

};

fetch('/notices',
{
  method: 'GET',

  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});

```

```ruby
require 'rest-client'
require 'json'

headers = {
  'Accept' => '*/*'
}

result = RestClient.get '/notices',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Accept': '*/*'
}

r = requests.get('/notices', params={

}, headers = headers)

print r.json()

```

```java
URL obj = new URL("/notices");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("GET");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());

```

```go
package main

import (
       "bytes"
       "net/http"
)

func main() {

    headers := map[string][]string{
        "Accept": []string{"*/*"},
        
    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("GET", "/notices", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

`GET /notices`

*Initialization API*

API to fetch all the notices in a paginated way

<h3 id="get__notices-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|electre.diffusion.backend.api.external.notice/offset|path|integer(int64)|true|none|
|electre.diffusion.backend.api.external.notice/limit|path|integer(int64)|true|none|

> Example responses

> 200 Response

<h3 id="get__notices-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Paginated notices|Inline|

<h3 id="get__notices-responseschema">Response Schema</h3>

Status Code **200**

*electre.diffusion.backend.api.external.notice/paginated-notices*

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» offset|integer(int64)|true|none|none|
|» limit|integer(int64)|true|none|none|
|» notices|[object]|true|none|none|
|»» electre.diffusion.domain.notice/notice|object|false|none|none|
|»»» autres-formats-ids|[any]|false|none|none|
|»»» identifiants|any|true|none|none|
|»»» auteurs|any|true|none|none|
|»»» editeur|string|true|none|none|
|»»» vedettes-matieres|any|false|none|none|
|»»» montant|object|false|none|none|
|»»»» qty|any|true|none|none|
|»»»» currency|any|true|none|none|
|»»» type-support|string|true|none|none|
|»»» id|string|true|none|none|
|»»» type-produit|string|false|none|none|
|»»» nouvelles-editions-ids|[any]|false|none|none|
|»»» mentions-edition|[string]|false|none|none|
|»»» collections|any|false|none|none|
|»»» support|string|true|none|none|
|»»» titre|string|true|none|none|
|»»» date-parution|any|false|none|none|
|»»» groupe-titres|any|true|none|none|
|»»» genre|[string]|true|none|none|

*anyOf*

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|»»»» *anonymous*|[string]|false|none|none|

*or*

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|»»»» *anonymous*|any|false|none|none|

*continued*

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|»»» quatrieme-couv|object|false|none|none|
|»»»» notice-ref|string|true|none|none|
|»»»» infoediteur|string|false|none|none|
|»»»» updated-by|string|false|none|none|
|»»»» updated-at|any|false|none|none|
|»»»» created-at|any|false|none|none|
|»»»» presentation|string|true|none|none|
|»»»» biographies|[object]|false|none|none|
|»»»»» electre.diffusion.domain.value.quatrieme-couv/biographie|object|false|none|none|
|»»»»»» langue|string|true|none|none|
|»»»»»» value|string|true|none|none|
|»»»»» created-by|string|false|none|none|
|»»»»» langue|string|true|none|none|
|»»»» editeurs|any|true|none|none|
|»»»» table-matieres|object|false|none|none|
|»»»»» notice-ref|string|true|none|none|
|»»»»» heads|[object]|true|none|none|
|»»»»»» electre.diffusion.domain.value.table-matieres/head|object|false|none|none|
|»»»»»»» text|string|true|none|none|
|»»»»»»» level|string|true|none|none|
|»»»»»» tocitems|[object]|true|none|none|
|»»»»»»» electre.diffusion.domain.value.table-matieres/tocitem|object|false|none|none|
|»»»»»»»» text|string|true|none|none|
|»»»»»»»» level|string|true|none|none|
|»»»»»»»» page|any|true|none|none|
|»»»»»»» created-at|any|false|none|none|
|»»»»»»» updated-at|any|false|none|none|
|»»»»»»» created-by|string|false|none|none|
|»»»»»»» updated-by|string|false|none|none|
|»»»»»» series|any|false|none|none|
|»»»»»» public|any|true|none|none|

*anyOf*

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|»»»»»»» *anonymous*|any|false|none|none|

*or*

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|»»»»»»» *anonymous*|[string]|false|none|none|

*continued*

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|»»»»»» theme-details|string|true|none|none|
|»»»»»» theme|string|true|none|none|
|»»»»»» notice-id|any|true|none|none|
|»»»»»» type-fichiers|[any]|true|none|none|
|»»»»»» disponibilite|any|true|none|none|
|»»»»»» anciennes-editions-ids|[any]|false|none|none|
|»»»»»» resume|string|false|none|none|

#### Enumerated Values

|Property|Value|
|---|---|
|type-produit|document-audio|
|type-produit|papeterie|
|type-produit|film|
|type-produit|carte|
|type-produit|jeu|
|type-produit|e-book|
|type-produit|poche|
|type-produit|jeu-video|
|type-produit|logiciel-educatif|
|type-produit|musique|
|type-produit|revue|
|type-produit|livre|
|type-produit|IAD|
|support|Document Vidéo|
|support|Fichier numérique|
|support|Imagerie papeterie|
|support|Livre|
|support|Pack librairie|
|support|Feuille planche|
|support|Revue|
|support|Jeux non électronique|
|support|Document audio|
|support|Logiciel|
|support|Carto|
|support|Musique imprimée|
|level|0|
|level|1|
|level|4|
|level|3|
|level|2|
|level|0|
|level|1|
|level|4|
|level|3|
|level|2|

<aside class="success">
This operation does not require authentication
</aside>

