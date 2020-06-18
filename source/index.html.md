---
title: Electre API v1.0.0
language_tabs:
  - shell: Shell
  - http: HTTP
  - javascript: JavaScript
  - ruby: Ruby
  - python: Python
  - php: PHP
  - java: Java
  - go: Go
toc_footers: []
includes: []
search: true
highlight_theme: darkula
headingLevel: 2

---

<!-- Generator: Widdershins v3.6.6 -->

<h1 id="electre-api">Electre API v1.0.0</h1>

> Scroll down for code samples, example requests and responses. Select a language for code samples from the tabs above or the mobile navigation menu.

Base URLs:

* <a href="https://api.electre-ng.com">https://api.electre-ng.com</a>

Email: <a href="mailto:api@electre.com">Electre API Team</a> Web: <a href="https://www.electre.com">Electre API Team</a> 

# Authentication

- oAuth2 authentication. 

    - Flow: password

    - Token URL = [https://login.electre-ng.com/auth/realms/electre/protocol/openid-connect/token](https://login.electre-ng.com/auth/realms/electre/protocol/openid-connect/token)

|Scope|Scope Description|
|---|---|
|read|Grants read access to notices|
|write|Grants write access to notices|

<h1 id="electre-api-notices">Notices</h1>

## GET _notices

<a id="opIdGET /notices"></a>

> Code samples

```shell
# You can also use wget
curl -X GET https://api.electre-ng.com/notices \
  -H 'Accept: */*' \
  -H 'Authorization: Bearer {access-token}'

```

```http
GET https://api.electre-ng.com/notices HTTP/1.1
Host: api.electre-ng.com
Accept: */*

```

```javascript

const headers = {
  'Accept':'*/*',
  'Authorization':'Bearer {access-token}'

};

fetch('https://api.electre-ng.com/notices',
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
  'Accept' => '*/*',
  'Authorization' => 'Bearer {access-token}'
}

result = RestClient.get 'https://api.electre-ng.com/notices',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Accept': '*/*',
  'Authorization': 'Bearer {access-token}'
}

r = requests.get('https://api.electre-ng.com/notices', headers = headers)

print(r.json())

```

```php
<?php

require 'vendor/autoload.php';

$headers = array(
    'Accept' => '*/*',
    'Authorization' => 'Bearer {access-token}',
    
    );

$client = new \GuzzleHttp\Client();

// Define array of request body.
$request_body = array();

try {
    $response = $client->request('GET','https://api.electre-ng.com/notices', array(
        'headers' => $headers,
        'json' => $request_body,
       )
    );
    print_r($response->getBody()->getContents());
 }
 catch (\GuzzleHttp\Exception\BadResponseException $e) {
    // handle exception or api errors.
    print_r($e->getMessage());
 }

 // ...

```

```java
URL obj = new URL("https://api.electre-ng.com/notices");
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
        "Authorization": []string{"Bearer {access-token}"},
        
    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("GET", "https://api.electre-ng.com/notices", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

`GET /notices`

*Notices Initialization endpoint*

API to fetch all the notices in a paginated way

                                                                                    * test list
                                                                                    * test list2

                                                                                    [Test Liens](https://www.grodziski.com)

<h3 id="get-_notices-parameters">Parameters</h3>

|Name|In|Type|Required|Description|Example|Min|Max|Default|
|---|---|---|---|---|---|---|---|---|
|offset|query|integer(int64)|false|Offset pour la page appelée|150|0|-|0|
|limit|query|integer(int64)|false|Quantité maximale de notices par page|20|0|1000|100|

> Example responses

> 200 Response

<h3 id="get-_notices-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Notices paginees|Inline|

<h3 id="get-_notices-responseschema">Response Schema</h3>

Status Code **200**

|Name|Type|Required|Restrictions|Description|Example|Min|Max|Default|
|---|---|---|---|---|---|---|---|---|
|» offset|integer(int64)|true|none|Offset, tel que passé en paramètre|none|none|none|none|
|» limit|integer(int64)|true|none|Quantité maximale de notices par page tel que passé en paramètre|none|none|none|none|
|» total|integer(int64)|true|none|Nombre total de notices|none|none|none|none|
|» notices|[object]|true|none|Liste des notices renvoyées par la requête, une notice regroupe l'ensemble des données commerciales, bibliographiques et de classement|Ex : 9782070144327|none|none|none|
|»» supportEtendu|object|false|none|none|Ex : 9782290102350|none|none|none|
|»»» supportEtenduId|string|true|none|code du support étendu (classification étendue, granularité plus fine que celle du code support : ce support est équivalent à celui du portail V2 actuel)|IFN|none|none|none|
|»»» libelleSupportEtendu|string|true|none|libellé du support étendu|Fichier numérique à télécharger de type « Ecrit » (texte + images fixes)|none|none|none|
|»» flagScolaire|boolean|false|none|Indique si l'ouvrage est un ouvrage scolaire au sens juridique du terme (true)<br>Les livres scolaires font l’objet de dispositions juridiques particulières au regard de la loi sur le prix unique du livre (loi du 10 août 1981) et de la loi sur le droit de prêt (loi du 18 juin 2003).<br>Le décret 2004-922 du 31 août 2004 a reprécisé la définition du livre scolaire pour l’application de ces dispositions.|"false"<br><br>Ex article avec le flag scolaire à "true" =  9782210167285|none|none|none|
|»» rayonsClient|[object]|false|none|classification personalisée de l'organisation calculée à partir des index Electre, pour un usage donné (site web, PIM, système de gestion...)|Ex : 9782070144327|none|none|none|
|»»» usageRayonId|string|true|none|destination de la classification (site web, système de gestion, etc.)|Gestion<br><br>Autres valeurs : "Web"|none|none|none|
|»»» rayonClientId|string|true|none|code du rayon dans la classification|8530000 (RC CORA)<br>691201001 (CODELEC)|none|none|none|
|»»» libelleRayonClient|string|true|none|Libellé dans la classification de l'organisation|FICTION / ROMAN - FICTION / ROMAN - GRAND FORMAT (RC CORA)<br>ROMANS ET NOUVELLES GRAND FORMAT (CODELEC)|none|none|none|
|»» catalogue|string|true|none|Ouvrage issu du catalogue : livre, musique, film, jeuxVidéo|Livre<br><br>Autres valeurs possibles :<br><br>Musique<br>Film<br>Jeux-vidéo|none|none|none|
|»» mentionsEdition|string|false|none|Mentions d'édition précisant une caractéristique de l'édition (révisée, nouvelle, augmentée...)|Nouvelle édition révisée et augmentée|none|none|none|
|»» dateParution|string|false|none|Date de parution au format YYYY-MM-DD|2018-10-11|none|none|none|
|»» prixDeLancement|object|false|none|Prix de lancement de l'ouvrage|Ex : 9782070144327|none|none|none|
|»»» devise|string|true|none|Code ISO de la devise|EUR|none|none|none|
|»»» taxes|[object]|false|none|Détail des taxes|none|none|none|none|
|»»»» taxeId|string|true|none|Identifiant la taxe|TVA|none|none|none|
|»»»» horsTaxe|number(double)|true|none|montant de lancement hors taxe sur lequel la taxe s'applique|52.13|none|none|none|
|»»»» tva|number(double)|true|none|tva sur le produit|5.5|none|none|none|
|»»» ttc|number(double)|true|none|montant de lancement TTC|55.00|none|none|none|
|»»» dateDebut|string|true|none|Début de la période durant laquelle le prix de lancement s'applique|2018-10-11|none|none|none|
|»»» dateFin|string|true|none|Fin de la période durant laquelle le prix de lancement s'applique|2019-03-31|none|none|none|
|»» quatriemeDeCouvertureResume|string|false|none|Résumé éditeur issu de la quatrième de couverture; <br>temporairement renseigné par un texte Electre <br>tant que la 4e n'est pas disponible|Ex : 9782070144327<br>\"Le disparu ou Amerika\" est un roman de formation. Il relate la vie de Karl Rossmann, 17 ans, expédié à New York par ses parents et qui trouve auprès d'un oncle providentiel un abri provisoire. \"Le procès\" relate les mésaventures de Joseph K, mis aux arrêts sans raison. \"Le château\" raconte les déboires de l'arpenteur K avec l'administration du château. Romans posthumes. ©Electre 2020|none|none|none|
|»» clilFel|object|false|none|Classification CLIL issue de Dilicom|Ex : 9782070144327|none|none|none|
|»»» clilFelId|string|true|none|code CLIL FEL (Dilicom)|3436|none|none|none|
|»»» libelleClilFel|string|true|none|libellé CLIL FEL (Dilicom)|Littérature générale -- Oeuvres classiques|none|none|none|
|»» anneeEdition|string|false|none|Année d'édition au format YYYY|2018|none|none|none|
|»» quatriemeDeCouverture|string|false|none|Résumé éditeur issu de la quatrième de couverture|9782070144327 (article sans 4e de couv)<br><br>Ex avec 4e de couv<br>9782330127121<br>Alphonse, quatorze ans, a disparu. Pendant que sa famille le cherche désespérément, il marche le long d'un chemin de campagne et fait face à la plus grande expérience de sa jeune vie : l'invisible. Même si rien ni personne ne l'avait préparé à une telle rencontre, voilà que surgissent en lui, à travers les forces de la nuit, des personnages réels et imaginaires peuplant les coulisses du rêve et de l'amour : Pierre-Paul-René, Judith, Walter, Victor, la grotte...<br><br>Alphonse est la porte d'entrée d'un univers littéraire insondable, où les vertiges de l'écriture sont éblouissants.|none|none|none|
|»» imageBlurCouverture|string|false|none|"Blurhash" de l'image de couverture (https://blurha.sh)|none|none|none|none|
|»» collections|[object]|false|none|collection d'ouvrages chez un éditeur<br>Ce champ est aussi utilisé pour diffuser les revues|Ex : 9782070144327|none|none|none|
|»»» collectionId|integer(int64)|true|none|identifiant de la collection|0-5184<br><br>Autre Ex : 9782290102343 : 0-6195|none|none|none|
|»»» libelleCollection|string|true|none|libellé de la collection|Bibliothèque de la Pléiade<br><br>Autre Ex : 9782290102343 : "J'ai lu"|none|none|none|
|»»» ISSN|string|false|none|code ISSN de la collection|0768-0562<br><br>Autre Ex : 9782290102343 : "0291-3623"|none|none|none|
|»»» NoDeCollection|string|false|none|numéro de l'ouvrage dans la collection|282|none|none|none|
|»»» sousCollection|object|false|none|sous-collection d'ouvrages chez un éditeur|Ex : 9782290102343|none|none|none|
|»»»» sousCollectionId|integer(int64)|true|none|identifiant de la sous-collection|0-6237|none|none|none|
|»»»» libelleSousCollection|string|true|none|libellé de la sous-collection|Fantasy|none|none|none|
|»»»» ISSNSousCollection|string|false|none|code ISSN de la sous-collection|1290-6697|none|none|none|
|»»»» NoDeSousCollection|string|false|none|numéro de l'ouvrage dans la sous-collection|none|none|none|none|
|»» descriptionsEbook|[object]|false|none|caractéristiques d'un livre numérique|Ex : 9782326052307|none|none|none|
|»»» formatEbook|string|true|none|format numérique; en cas de pack numérique, tous les formats du pack sont exposés|EPUB<br><br>Autres formats Ebook possibles :<br><br>PDF<br>mobipocket<br>streaming<br>pack multiformat (+ formats compris dans le pack)|none|none|none|
|»»» protectionEbook|string|false|none|type de protection de l'ebook|DRM Adobe|none|none|none|
|»»» droitsEbook|[object]|false|none|droits de l'ebook|Ex : 9782326052307|none|none|none|
|»»»» utilisation|string|true|none|none|impression<br>copier-coller<br>partage|none|none|none|
|»»»» limitation|string|true|none|none|interdiction<br>interdiction<br>autorisation sans limite|none|none|none|
|»»» resumeEbook|string|false|none|résumé du livre et/ou texte de l'équivalent 4ème de couverture|Ex : 9782290102367 (idem notice livre imprimé 9782290102343) : "On dit que les mercenaires n’ont pas d’âme, mais ils ont une mémoire. La nôtre, celle de la dernière des compagnies franches de Khatovar, vous la tenez entre vos mains. Ce sont nos entrailles, chaudes et puantes, étalées là devant vous. Vous qui lisez ces annales, ne perdez pas votre temps à nous maudire, car nous le sommes déjà..."|none|none|none|
|»»» poidsEbook|string|false|none|poids en mégaoctets du fichier numérique|4.812|none|none|none|
|»»» formatsEbookContenus|[object]|false|none|none|Ex : 9782820526120|none|none|none|
|»»»» eanEbookContenu|[string]|true|none|none|3612221838859<br>3612221838842<br>3612221838866|none|none|none|
|»»»» formatEbookContenu|string|true|none|none|EPUB<br>Mobipocket<br>Streaming|none|none|none|
|»»»» protectionEbookContenu|string|false|none|none|filigrane numérique<br>filigrane numérique<br>DRM|none|none|none|
|»»»» droitsEbookContenu|[object]|false|none|none|none|none|none|none|
|»»»»» utilisation|string|true|none|none|3612221838859<br>impression<br>copier-coller<br>partage<br><br>3612221838842<br>impression<br>copier-coller<br>partage<br><br>3612221838866<br>impression<br>copier-coller|none|none|none|
|»»»»» limitation|string|true|none|none|3612221838859<br>autorisation sans limite<br>autorisation sans limite<br>autorisation sans limite<br><br>3612221838842<br>autorisation sans limite<br>autorisation sans limite<br>autorisation sans limite<br><br>3612221838866<br>interdiction<br>autorisation sans limite|none|none|none|
|»»»» descriptionEbookContenu|string|false|none|none|ePub avec Watermark<br><br>Mobipocket avec Watermark<br><br>Accès streaming : format vous permettant d'accéder en streaming aux ouvrages via notre liseuse web. Pour accéder à ce format, vous devez impérativement disposer d'une connexion à l'Internet et d'une largeur d'écran supérieure à 800 pixels. Actuellement compatible avec Firefox 3 ou supérieur, Safari 4 et Internet Explorer 7 ou supérieur.|none|none|none|
|»»»» venduSeul|boolean|false|none|none|false<br>false<br>false|none|none|none|
|»»»» poidsEbookContenu|number(double)|false|none|none|0.481<br>1.528<br>-|none|none|none|
|»» image160pxCouverture|string|false|none|URL de l'imagette desktop de la couverture au format JPG de taille 160 pixels de large|none|none|none|none|
|»» support|object|false|none|Support de l'article  (classification simple: ce support est celui du type de produits proposé sur Electre NG et qui permet de distinguer les types de produits différents d'un livre papier dans une liste de résultat ou dans une notice)<br>Un seul support par article.|Ex : 9782070144327|none|none|none|
|»»» supportId|string|true|none|code du support|LIV|none|none|none|
|»»» libelleSupport|string|true|none|description du support|"Livre"<br><br>liste complète libellés support : Revue, Musique, Livre, Poche, Document audio, impression à la demande, jeu, papeterie, film, logiciel éducatif, carte et plan, E-Book PDF, E-Book e-PUB, E-Book Mobipocket, E-Book streaming, E-Book pack multiformat (+ formats compris dans le pack) , Jeu video, Coffret (de livres grand format ou de livres de poche)<br><br>Autre Ex : 9782290102350 : "E-BOOK ePub"|none|none|none|
|»» titre|string|true|none|Titre complet de l'ouvrage construit à partir de plusieurs titres|Ex : 9782070144327 : Oeuvres complètes. Volume 2, Romans|none|none|none|
|»» rayonsElectreEtendu|[object]|false|none|classification étendue (env. 750 entrées)|Ex : 9782070144327|none|none|none|
|»»» rayonElectreEtenduId|string|true|none|code rayon Electre, classification étendue|12LI0H|none|none|none|
|»»» libelleRayonElectreEtendu|string|true|none|libellé rayon Electre, classification étendue|Littérature -- Divers Littérature -- Pléiade étrangers|none|none|none|
|»» imageCouverture|string|false|none|URL de l'image de la couverture au format JPG à la taille maximale|none|none|none|none|
|»» extraitPlayer|string|false|none|Extrait + player consommés ensemble (URL)|Ex : 9782290102343|none|none|none|
|»» imagetteCouverture|string|false|none|URL de l'imagette mobile de la couverture au format JPG de taille 80 pixels de large|none|none|none|none|
|»» biographies|[object]|false|none|courte biographie de l'auteur, issue de la quatrième de couverture (dans les différentes langues si la bio est en plusieurs langues)|Ex : 9782290102343|none|none|none|
|»»» langue|string|true|none|langue de la biographie ("fre", "eng" ou "xxx"); ce champs n'est pas forcément à afficher mais permet de séparer en affichage les différentes versions de langue|"fre"|none|none|none|
|»»» biographie|string|true|none|texte de la biographie|Né à New York en 1944, Glen Cook peut se vanter d'avoir durablement marqué la fantasy. Tant dans leur forme que par leur propos d'une noirceur sans égal, Les annales de la Compagnie noire font partie de ces oeuvres dont on dit qu'il y a un avant et un après.|none|none|none|
|»» distributeur|object|false|none|Distributeur|Ex : 9782070144327|none|none|none|
|»»» distributeurId|integer(int64)|true|none|identifiant du distributeur Electre|0-48441|none|none|none|
|»»» distributeurNoticeRef|string|true|none|Référence de la notice chez le distributeur|A14432|none|none|none|
|»»» globalLocationNumber|string|true|none|code distributeur GLN (Global Location Number)|3012600500000|none|none|none|
|»»» raisonSociale|string|true|none|raison sociale du distributeur|Sodis|none|none|none|
|»» editeurs|[object]|true|none|Editeurs|Ex : 9782070144327|none|none|none|
|»»» editeurId|integer(int64)|true|none|identifiant Electre de l'éditeur|0-71483|none|none|none|
|»»» raisonSociale|string|true|none|raison sociale de l'éditeur|Gallimard|none|none|none|
|»»» lieuPublication|string|true|none|Ville du lieu d'édition|Paris|none|none|none|
|»» source|string|true|none|Source de la notice (electre, btlf, olf, dilicom)<br>Les sources disponibles dépendent de l'abonnement souscrit.|Electre<br><br>Autres valeurs possibles :<br><br>BTLF<br>OLF<br>FEL|none|none|none|
|»» coffret|boolean|false|none|none|Ex : 9782409024290 : Coffret = "true"|none|none|none|
|»» felLibelleCaisse|string|false|none|Désignation   courte   du   produit   (20   caractères)   permettant   au   consommateur de faire le rapprochement entre les articles achetés et les lignes de son ticket de caisse.|ROMANS KAFKA|none|none|none|
|»» extrait|string|false|none|URL vers le binaire du fichier epub ou PDF|Ex : 9782290102343|none|none|none|
|»» rayonsElectre|[object]|false|none|classification simple (env. 200 entrées)|Ex : 9782070144327|none|none|none|
|»»» rayonElectreId|string|true|none|code rayon Electre, classification simple|R0102|none|none|none|
|»»» libelleRayonElectre|string|true|none|libellé rayon Electre, classification simple|Littérature -- Romans étrangers|none|none|none|
|»» series|[object]|false|none|série d'ouvrages chez un éditeur donné|none|none|none|none|
|»»» serieId|string|true|none|identifiant de la série|0-358619|none|none|none|
|»»» titreSerie|string|true|none|titre de la série|Oeuvres complètes|none|none|none|
|»»» numeroSerie|string|false|none|rang de l'ouvrage dans la série|2|none|none|none|
|»»» serieIssn|string|false|none|N° ISSN de la série|none|none|none|none|
|»» noticeId|integer(int64)|true|none|Identifiant de la notice chez Electre|0-5325984|none|none|none|
|»» isbns|[string]|false|none|International Standard Book Number|978-2-07-014432-7<br><br>Cas d'un article avec deux EAN : <br><br>978-2-330-12712-1<br>978-2-7609-1322-6|none|none|none|
|»» felCodeRetour|string|false|none|Code indiquant si cet article peut être ou non retourné.<br>- "retour-possible-selon-CGV" (code retour Dilicom 1)<br>- "retour-interdit" (code retour Dilicom 2)<br>- "retour-interdit-sauf-accord-cial" (code retour Dilicom 3)<br>- "retour-sur-couverture" (code retour Dilicom 5)<br>- "retour-sur-couverture-obligatoire" (code retour Dilicom 6)|3|none|none|none|
|»» eans|[string]|true|none|Identifiants EAN de l'ouvrage (plusieurs EAN possibles)|9782070144327<br>       <br>Cas d'un article avec deux EAN : <br><br>9782330127121<br>9782760913226|none|none|none|
|»» auteursPrincipaux|[object]|false|none|auteurs principaux de l'ouvrage|Ex : 9782070144327|none|none|none|
|»»» auteurId|string|true|none|identifiant de l'auteur|0-1254743|none|none|none|
|»»» nom|string|false|none|nom de l'auteur|Franz|none|none|none|
|»»» prenom|string|false|none|prénom de l'auteur|Kafka|none|none|none|
|»»» formebib|string|true|none|forme bibliographique du nom de l'auteur|Kafka, Franz|none|none|none|
|»»» typeContribution|string|true|none|Type de contribution principale (Auteur, Adaptateur, Producteur, etc.), <br>Enumerated values in: ["Auteur", "Auteur (photographe)", "Auteur (illustrateur)", "Interviewer", "Personne interviewée", "Auteur du texte", "Auteur originel", "Auteur adapté", "Adaptateur", "Auteur douteux, prétendu", "Auteur (artiste)", "Librettiste", "Parolier", "Compositeur", "Programmeur", "Infographiste", "Scénariste", "Dialoguiste", "Concepteur", "Producteur", "Réalisateur de film"]|Auteur (Auteur = libelle du code contribution A01)<br>Auteur (photographe = libellé du code contribution A11)|none|none|none|
|»»» nationalites|[object]|false|none|nationalités de l'auteur|Nationalité figurant sur le passeport<br>Tchèque, République, Grande-Breagne (et non pas Ecosse ou Pays de Galle)|none|none|none|
|»»» qualificatifs|[string]|false|none|date de naissance, date de mort, titre nobiliaire...|1883-1924|none|none|none|
|»»» idBNF|string|false|none|identifiant BNF de l'auteur|11909301|none|none|none|
|»» genres|[object]|false|none|Indexation genre de la base Electre|Ex : 9782070144327|none|none|none|
|»»» genreId|string|true|none|Code pour toute la branche|GLET001|none|none|none|
|»»» libelleGenre|string|true|none|Libellé de toute la branche|Littératures et textes étrangers classiques -- Traduction en français|none|none|none|
|»» felImpressionDemande|boolean|false|none|désigne les articles en impression à la demande. L'IAD est aussi un type de produit envoyé dans le champ "support"|Ex1 : 9782070144327 : Impression à la demande  = "false"<br><br>Ex2 : 9782010144097 : Impression à la demande  = "true"|none|none|none|
|»» prix|object|true|none|Prix de vente de l'ouvrage|Ex : 9782070144327|none|none|none|
|»»» devise|string|true|none|Code ISO de la devise|EUR|none|none|EUR|
|»»» taxes|[object]|false|none|Détail des taxes : TVA sur le livre (ou sur un autre type de produit si l'article comprend d'autres types de produits)|none|none|none|none|
|»»»» taxeId|string|true|none|Identifiant de la taxe (TVA)|TVA|none|none|none|
|»»»» horsTaxe|number(double)|true|none|Montant hors taxe sur lequel la taxe s'applique|56.87|0|-|none|
|»»»» tva|number(double)|true|none|Taux de taxe appliqué|5.5|none|none|none|
|»»» ttc|number(double)|true|none|Montant TTC|60.00|none|none|none|
|»» descriptionPhysique|object|false|none|caractéristiques physiques de l'article|Ex : 9782070144327|none|none|none|
|»»» nbPages|integer(int64)|false|none|nombre de pages|XXIV-1051|none|none|none|
|»»» largeur|number(double)|false|none|largeur de l'ouvrage, en centimètres|11|none|none|none|
|»»» hauteur|number(double)|false|none|hauteur de l'ouvrage, en centimètres|17|none|none|none|
|»»» epaisseur|number(double)|false|none|épaisseur de l'ouvrage, en centimètres|3.0|none|none|none|
|»»» mentionIllustrations|string|false|none|types d'illustrations (illustrations en couleur, en noir et blanc)|Ex : 9782203191143 : illustrations en couleur|none|none|none|
|»»» poids|integer(int64)|false|none|poids de l'ouvrage, en grammes|444|none|none|none|
|»»» reliure|string|false|none|type de reliure de l'ouvrage|Relié sous étui|none|none|none|
|»» flagFiction|boolean|false|none|Indique s'il s'agit d'un ouvrage de fiction ou non.|"true"<br><br>Ex article avec le flag fiction à "false" =  9782210167285|none|none|none|
|»» disponibilite|string|true|none|Disponibilité de l'ouvrage, Enumerated values in: [\"epuise\", \"manquan\t", \"a-paraitre\", \"disponible\"]|disponible<br><br>Autres valeurs possibles : <br><br>épuisé <br>à paraître <br>manquant|none|none|none|
|»» desactive|boolean|true|none|Indique si la notice a existée mais a été désactivée. Toujours à FALSE pour le endpoint /init, parfois à TRUE pour le endpoint /updated.|none|none|none|none|
|»» disponibiliteEtendue|object|true|none|Disponibilité de l'ouvrage, <br>Enumerated values in:<br> [\"epuise\", \"arret de commercialisation\", \"ne sera plus distribue\", \"reimpression en cours\", \"manque provisoirement\", \"a-paraitre\", \"disponible\"]|Valeurs possibles :<br><br>1 = disponible<br>2 = à paraître<br>3 = réimpression en cours<br>4 = manque provisoirement <br>5 = épuisé<br>6 = arrêt de commercialisation <br>7 = ne sera plus distribué<br>8 = à reparaitre|none|none|none|
|»»» disponibiliteEtendueId|integer(int64)|true|none|Valeur de disponibilité parmis 1,2 ,3 ,4, 5, 6, 7 ,8, 9<br>Mapping :<br>disponible                1<br>a-paraitre                 2<br>reimpression-en-cours      3<br>manque-provisoirement    4<br>epuise                     5<br>arret-de-commercialisation 6<br>ne-sera-plus-distribue     7<br>a-reparaitre               8<br>parution-annulee       9|1|none|none|none|
|»»» disponibiliteEtendueLibelle|string|true|none|Valeur de disponibilité parmis <br>- disponible <br>- a-paraitre <br>- reimpression-en-cours    <br>- manque-provisoirement <br>- epuise <br>- arret-de-commercialisation <br>- ne-sera-plus-distribue <br>- a-reparaitre <br>- parution-annulee|disponible|none|none|none|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
OAuth2 ( Scopes: read )
</aside>

## GET notices_updated

<a id="opIdGET notices/updated"></a>

> Code samples

```shell
# You can also use wget
curl -X GET https://api.electre-ng.com/notices/updated?from=string&lastndays=0 \
  -H 'Accept: */*' \
  -H 'Authorization: Bearer {access-token}'

```

```http
GET https://api.electre-ng.com/notices/updated?from=string&lastndays=0 HTTP/1.1
Host: api.electre-ng.com
Accept: */*

```

```javascript

const headers = {
  'Accept':'*/*',
  'Authorization':'Bearer {access-token}'

};

fetch('https://api.electre-ng.com/notices/updated?from=string&lastndays=0',
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
  'Accept' => '*/*',
  'Authorization' => 'Bearer {access-token}'
}

result = RestClient.get 'https://api.electre-ng.com/notices/updated',
  params: {
  'from' => 'string',
'lastndays' => 'integer(int64)'
}, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Accept': '*/*',
  'Authorization': 'Bearer {access-token}'
}

r = requests.get('https://api.electre-ng.com/notices/updated', params={
  'from': 'string',  'lastndays': '0'
}, headers = headers)

print(r.json())

```

```php
<?php

require 'vendor/autoload.php';

$headers = array(
    'Accept' => '*/*',
    'Authorization' => 'Bearer {access-token}',
    
    );

$client = new \GuzzleHttp\Client();

// Define array of request body.
$request_body = array();

try {
    $response = $client->request('GET','https://api.electre-ng.com/notices/updated', array(
        'headers' => $headers,
        'json' => $request_body,
       )
    );
    print_r($response->getBody()->getContents());
 }
 catch (\GuzzleHttp\Exception\BadResponseException $e) {
    // handle exception or api errors.
    print_r($e->getMessage());
 }

 // ...

```

```java
URL obj = new URL("https://api.electre-ng.com/notices/updated?from=string&lastndays=0");
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
        "Authorization": []string{"Bearer {access-token}"},
        
    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("GET", "https://api.electre-ng.com/notices/updated", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

`GET /notices/updated`

*Updated Notices endpoint*

API to fetch the updated notices in a period in a paginated way

<h3 id="get-notices_updated-parameters">Parameters</h3>

|Name|In|Type|Required|Description|Example|Min|Max|Default|
|---|---|---|---|---|---|---|---|---|
|offset|query|integer(int64)|false|Offset pour la page appelée|0|0|1000|100|
|limit|query|integer(int64)|false|Quantité maximale de notices par page|20|0|-|0|
|from|query|string|true|timestamp au format YYYY-MM-DD-HH:mm:ss filtrant toutes les notices modifiées ou créés depuis ce timestamp.|2020-01-01|none|none|-|
|to|query|string|false|timestamp au format YYYY-MM-DD-HH:mm:ss filtrant toutes les notices modifiées ou créées jusqu`à ce timestamp (inclus). Si ce paramètre est absent, on considère l'instant courant.|2020-01-04|none|none|-|
|lastndays|query|integer(int64)|true|nombre entier positif indiquant la période de filtre, le jour courant n'est pas pris en compte dans le filtre (ex: last-n-days=2 exécuté le 3 janvier 2020 filtre les notices modifiées le 1 et 2 janvier, en pratique équivalent à from=2020-01-01). C'est un paramètre de confort pour indiquer facilement les derniers jours sur lesquels le client souhaite avoir les notices modifiées.|5|0|none|-|

#### Detailed descriptions

**lastndays**: nombre entier positif indiquant la période de filtre, le jour courant n'est pas pris en compte dans le filtre (ex: last-n-days=2 exécuté le 3 janvier 2020 filtre les notices modifiées le 1 et 2 janvier, en pratique équivalent à from=2020-01-01). C'est un paramètre de confort pour indiquer facilement les derniers jours sur lesquels le client souhaite avoir les notices modifiées.
Les parameters from et to peuvent être utilisés de manière indépendante ou conjointe.
Au moins un des paramètres from ou lastndays est obligatoire, si lastndays est présent il a la priorité sur les paramètres from et to.

> Example responses

> 200 Response

<h3 id="get-notices_updated-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Notices paginees|Inline|

<h3 id="get-notices_updated-responseschema">Response Schema</h3>

Status Code **200**

|Name|Type|Required|Restrictions|Description|Example|Min|Max|Default|
|---|---|---|---|---|---|---|---|---|
|» offset|integer(int64)|true|none|Offset, tel que passé en paramètre|none|none|none|none|
|» limit|integer(int64)|true|none|Quantité maximale de notices par page tel que passé en paramètre|none|none|none|none|
|» total|integer(int64)|true|none|Nombre total de notices|none|none|none|none|
|» notices|[object]|true|none|Liste des notices renvoyées par la requête, une notice regroupe l'ensemble des données commerciales, bibliographiques et de classement|Ex : 9782070144327|none|none|none|
|»» supportEtendu|object|false|none|none|Ex : 9782290102350|none|none|none|
|»»» supportEtenduId|string|true|none|code du support étendu (classification étendue, granularité plus fine que celle du code support : ce support est équivalent à celui du portail V2 actuel)|IFN|none|none|none|
|»»» libelleSupportEtendu|string|true|none|libellé du support étendu|Fichier numérique à télécharger de type « Ecrit » (texte + images fixes)|none|none|none|
|»» flagScolaire|boolean|false|none|Indique si l'ouvrage est un ouvrage scolaire au sens juridique du terme (true)<br>Les livres scolaires font l’objet de dispositions juridiques particulières au regard de la loi sur le prix unique du livre (loi du 10 août 1981) et de la loi sur le droit de prêt (loi du 18 juin 2003).<br>Le décret 2004-922 du 31 août 2004 a reprécisé la définition du livre scolaire pour l’application de ces dispositions.|"false"<br><br>Ex article avec le flag scolaire à "true" =  9782210167285|none|none|none|
|»» rayonsClient|[object]|false|none|classification personalisée de l'organisation calculée à partir des index Electre, pour un usage donné (site web, PIM, système de gestion...)|Ex : 9782070144327|none|none|none|
|»»» usageRayonId|string|true|none|destination de la classification (site web, système de gestion, etc.)|Gestion<br><br>Autres valeurs : "Web"|none|none|none|
|»»» rayonClientId|string|true|none|code du rayon dans la classification|8530000 (RC CORA)<br>691201001 (CODELEC)|none|none|none|
|»»» libelleRayonClient|string|true|none|Libellé dans la classification de l'organisation|FICTION / ROMAN - FICTION / ROMAN - GRAND FORMAT (RC CORA)<br>ROMANS ET NOUVELLES GRAND FORMAT (CODELEC)|none|none|none|
|»» catalogue|string|true|none|Ouvrage issu du catalogue : livre, musique, film, jeuxVidéo|Livre<br><br>Autres valeurs possibles :<br><br>Musique<br>Film<br>Jeux-vidéo|none|none|none|
|»» mentionsEdition|string|false|none|Mentions d'édition précisant une caractéristique de l'édition (révisée, nouvelle, augmentée...)|Nouvelle édition révisée et augmentée|none|none|none|
|»» dateParution|string|false|none|Date de parution au format YYYY-MM-DD|2018-10-11|none|none|none|
|»» prixDeLancement|object|false|none|Prix de lancement de l'ouvrage|Ex : 9782070144327|none|none|none|
|»»» devise|string|true|none|Code ISO de la devise|EUR|none|none|none|
|»»» taxes|[object]|false|none|Détail des taxes|none|none|none|none|
|»»»» taxeId|string|true|none|Identifiant la taxe|TVA|none|none|none|
|»»»» horsTaxe|number(double)|true|none|montant de lancement hors taxe sur lequel la taxe s'applique|52.13|none|none|none|
|»»»» tva|number(double)|true|none|tva sur le produit|5.5|none|none|none|
|»»» ttc|number(double)|true|none|montant de lancement TTC|55.00|none|none|none|
|»»» dateDebut|string|true|none|Début de la période durant laquelle le prix de lancement s'applique|2018-10-11|none|none|none|
|»»» dateFin|string|true|none|Fin de la période durant laquelle le prix de lancement s'applique|2019-03-31|none|none|none|
|»» quatriemeDeCouvertureResume|string|false|none|Résumé éditeur issu de la quatrième de couverture; <br>temporairement renseigné par un texte Electre <br>tant que la 4e n'est pas disponible|Ex : 9782070144327<br>\"Le disparu ou Amerika\" est un roman de formation. Il relate la vie de Karl Rossmann, 17 ans, expédié à New York par ses parents et qui trouve auprès d'un oncle providentiel un abri provisoire. \"Le procès\" relate les mésaventures de Joseph K, mis aux arrêts sans raison. \"Le château\" raconte les déboires de l'arpenteur K avec l'administration du château. Romans posthumes. ©Electre 2020|none|none|none|
|»» clilFel|object|false|none|Classification CLIL issue de Dilicom|Ex : 9782070144327|none|none|none|
|»»» clilFelId|string|true|none|code CLIL FEL (Dilicom)|3436|none|none|none|
|»»» libelleClilFel|string|true|none|libellé CLIL FEL (Dilicom)|Littérature générale -- Oeuvres classiques|none|none|none|
|»» anneeEdition|string|false|none|Année d'édition au format YYYY|2018|none|none|none|
|»» quatriemeDeCouverture|string|false|none|Résumé éditeur issu de la quatrième de couverture|9782070144327 (article sans 4e de couv)<br><br>Ex avec 4e de couv<br>9782330127121<br>Alphonse, quatorze ans, a disparu. Pendant que sa famille le cherche désespérément, il marche le long d'un chemin de campagne et fait face à la plus grande expérience de sa jeune vie : l'invisible. Même si rien ni personne ne l'avait préparé à une telle rencontre, voilà que surgissent en lui, à travers les forces de la nuit, des personnages réels et imaginaires peuplant les coulisses du rêve et de l'amour : Pierre-Paul-René, Judith, Walter, Victor, la grotte...<br><br>Alphonse est la porte d'entrée d'un univers littéraire insondable, où les vertiges de l'écriture sont éblouissants.|none|none|none|
|»» imageBlurCouverture|string|false|none|"Blurhash" de l'image de couverture (https://blurha.sh)|none|none|none|none|
|»» collections|[object]|false|none|collection d'ouvrages chez un éditeur<br>Ce champ est aussi utilisé pour diffuser les revues|Ex : 9782070144327|none|none|none|
|»»» collectionId|integer(int64)|true|none|identifiant de la collection|0-5184<br><br>Autre Ex : 9782290102343 : 0-6195|none|none|none|
|»»» libelleCollection|string|true|none|libellé de la collection|Bibliothèque de la Pléiade<br><br>Autre Ex : 9782290102343 : "J'ai lu"|none|none|none|
|»»» ISSN|string|false|none|code ISSN de la collection|0768-0562<br><br>Autre Ex : 9782290102343 : "0291-3623"|none|none|none|
|»»» NoDeCollection|string|false|none|numéro de l'ouvrage dans la collection|282|none|none|none|
|»»» sousCollection|object|false|none|sous-collection d'ouvrages chez un éditeur|Ex : 9782290102343|none|none|none|
|»»»» sousCollectionId|integer(int64)|true|none|identifiant de la sous-collection|0-6237|none|none|none|
|»»»» libelleSousCollection|string|true|none|libellé de la sous-collection|Fantasy|none|none|none|
|»»»» ISSNSousCollection|string|false|none|code ISSN de la sous-collection|1290-6697|none|none|none|
|»»»» NoDeSousCollection|string|false|none|numéro de l'ouvrage dans la sous-collection|none|none|none|none|
|»» descriptionsEbook|[object]|false|none|caractéristiques d'un livre numérique|Ex : 9782326052307|none|none|none|
|»»» formatEbook|string|true|none|format numérique; en cas de pack numérique, tous les formats du pack sont exposés|EPUB<br><br>Autres formats Ebook possibles :<br><br>PDF<br>mobipocket<br>streaming<br>pack multiformat (+ formats compris dans le pack)|none|none|none|
|»»» protectionEbook|string|false|none|type de protection de l'ebook|DRM Adobe|none|none|none|
|»»» droitsEbook|[object]|false|none|droits de l'ebook|Ex : 9782326052307|none|none|none|
|»»»» utilisation|string|true|none|none|impression<br>copier-coller<br>partage|none|none|none|
|»»»» limitation|string|true|none|none|interdiction<br>interdiction<br>autorisation sans limite|none|none|none|
|»»» resumeEbook|string|false|none|résumé du livre et/ou texte de l'équivalent 4ème de couverture|Ex : 9782290102367 (idem notice livre imprimé 9782290102343) : "On dit que les mercenaires n’ont pas d’âme, mais ils ont une mémoire. La nôtre, celle de la dernière des compagnies franches de Khatovar, vous la tenez entre vos mains. Ce sont nos entrailles, chaudes et puantes, étalées là devant vous. Vous qui lisez ces annales, ne perdez pas votre temps à nous maudire, car nous le sommes déjà..."|none|none|none|
|»»» poidsEbook|string|false|none|poids en mégaoctets du fichier numérique|4.812|none|none|none|
|»»» formatsEbookContenus|[object]|false|none|none|Ex : 9782820526120|none|none|none|
|»»»» eanEbookContenu|[string]|true|none|none|3612221838859<br>3612221838842<br>3612221838866|none|none|none|
|»»»» formatEbookContenu|string|true|none|none|EPUB<br>Mobipocket<br>Streaming|none|none|none|
|»»»» protectionEbookContenu|string|false|none|none|filigrane numérique<br>filigrane numérique<br>DRM|none|none|none|
|»»»» droitsEbookContenu|[object]|false|none|none|none|none|none|none|
|»»»»» utilisation|string|true|none|none|3612221838859<br>impression<br>copier-coller<br>partage<br><br>3612221838842<br>impression<br>copier-coller<br>partage<br><br>3612221838866<br>impression<br>copier-coller|none|none|none|
|»»»»» limitation|string|true|none|none|3612221838859<br>autorisation sans limite<br>autorisation sans limite<br>autorisation sans limite<br><br>3612221838842<br>autorisation sans limite<br>autorisation sans limite<br>autorisation sans limite<br><br>3612221838866<br>interdiction<br>autorisation sans limite|none|none|none|
|»»»» descriptionEbookContenu|string|false|none|none|ePub avec Watermark<br><br>Mobipocket avec Watermark<br><br>Accès streaming : format vous permettant d'accéder en streaming aux ouvrages via notre liseuse web. Pour accéder à ce format, vous devez impérativement disposer d'une connexion à l'Internet et d'une largeur d'écran supérieure à 800 pixels. Actuellement compatible avec Firefox 3 ou supérieur, Safari 4 et Internet Explorer 7 ou supérieur.|none|none|none|
|»»»» venduSeul|boolean|false|none|none|false<br>false<br>false|none|none|none|
|»»»» poidsEbookContenu|number(double)|false|none|none|0.481<br>1.528<br>-|none|none|none|
|»» image160pxCouverture|string|false|none|URL de l'imagette desktop de la couverture au format JPG de taille 160 pixels de large|none|none|none|none|
|»» support|object|false|none|Support de l'article  (classification simple: ce support est celui du type de produits proposé sur Electre NG et qui permet de distinguer les types de produits différents d'un livre papier dans une liste de résultat ou dans une notice)<br>Un seul support par article.|Ex : 9782070144327|none|none|none|
|»»» supportId|string|true|none|code du support|LIV|none|none|none|
|»»» libelleSupport|string|true|none|description du support|"Livre"<br><br>liste complète libellés support : Revue, Musique, Livre, Poche, Document audio, impression à la demande, jeu, papeterie, film, logiciel éducatif, carte et plan, E-Book PDF, E-Book e-PUB, E-Book Mobipocket, E-Book streaming, E-Book pack multiformat (+ formats compris dans le pack) , Jeu video, Coffret (de livres grand format ou de livres de poche)<br><br>Autre Ex : 9782290102350 : "E-BOOK ePub"|none|none|none|
|»» titre|string|true|none|Titre complet de l'ouvrage construit à partir de plusieurs titres|Ex : 9782070144327 : Oeuvres complètes. Volume 2, Romans|none|none|none|
|»» rayonsElectreEtendu|[object]|false|none|classification étendue (env. 750 entrées)|Ex : 9782070144327|none|none|none|
|»»» rayonElectreEtenduId|string|true|none|code rayon Electre, classification étendue|12LI0H|none|none|none|
|»»» libelleRayonElectreEtendu|string|true|none|libellé rayon Electre, classification étendue|Littérature -- Divers Littérature -- Pléiade étrangers|none|none|none|
|»» imageCouverture|string|false|none|URL de l'image de la couverture au format JPG à la taille maximale|none|none|none|none|
|»» extraitPlayer|string|false|none|Extrait + player consommés ensemble (URL)|Ex : 9782290102343|none|none|none|
|»» imagetteCouverture|string|false|none|URL de l'imagette mobile de la couverture au format JPG de taille 80 pixels de large|none|none|none|none|
|»» biographies|[object]|false|none|courte biographie de l'auteur, issue de la quatrième de couverture (dans les différentes langues si la bio est en plusieurs langues)|Ex : 9782290102343|none|none|none|
|»»» langue|string|true|none|langue de la biographie ("fre", "eng" ou "xxx"); ce champs n'est pas forcément à afficher mais permet de séparer en affichage les différentes versions de langue|"fre"|none|none|none|
|»»» biographie|string|true|none|texte de la biographie|Né à New York en 1944, Glen Cook peut se vanter d'avoir durablement marqué la fantasy. Tant dans leur forme que par leur propos d'une noirceur sans égal, Les annales de la Compagnie noire font partie de ces oeuvres dont on dit qu'il y a un avant et un après.|none|none|none|
|»» distributeur|object|false|none|Distributeur|Ex : 9782070144327|none|none|none|
|»»» distributeurId|integer(int64)|true|none|identifiant du distributeur Electre|0-48441|none|none|none|
|»»» distributeurNoticeRef|string|true|none|Référence de la notice chez le distributeur|A14432|none|none|none|
|»»» globalLocationNumber|string|true|none|code distributeur GLN (Global Location Number)|3012600500000|none|none|none|
|»»» raisonSociale|string|true|none|raison sociale du distributeur|Sodis|none|none|none|
|»» editeurs|[object]|true|none|Editeurs|Ex : 9782070144327|none|none|none|
|»»» editeurId|integer(int64)|true|none|identifiant Electre de l'éditeur|0-71483|none|none|none|
|»»» raisonSociale|string|true|none|raison sociale de l'éditeur|Gallimard|none|none|none|
|»»» lieuPublication|string|true|none|Ville du lieu d'édition|Paris|none|none|none|
|»» source|string|true|none|Source de la notice (electre, btlf, olf, dilicom)<br>Les sources disponibles dépendent de l'abonnement souscrit.|Electre<br><br>Autres valeurs possibles :<br><br>BTLF<br>OLF<br>FEL|none|none|none|
|»» coffret|boolean|false|none|none|Ex : 9782409024290 : Coffret = "true"|none|none|none|
|»» felLibelleCaisse|string|false|none|Désignation   courte   du   produit   (20   caractères)   permettant   au   consommateur de faire le rapprochement entre les articles achetés et les lignes de son ticket de caisse.|ROMANS KAFKA|none|none|none|
|»» extrait|string|false|none|URL vers le binaire du fichier epub ou PDF|Ex : 9782290102343|none|none|none|
|»» rayonsElectre|[object]|false|none|classification simple (env. 200 entrées)|Ex : 9782070144327|none|none|none|
|»»» rayonElectreId|string|true|none|code rayon Electre, classification simple|R0102|none|none|none|
|»»» libelleRayonElectre|string|true|none|libellé rayon Electre, classification simple|Littérature -- Romans étrangers|none|none|none|
|»» series|[object]|false|none|série d'ouvrages chez un éditeur donné|none|none|none|none|
|»»» serieId|string|true|none|identifiant de la série|0-358619|none|none|none|
|»»» titreSerie|string|true|none|titre de la série|Oeuvres complètes|none|none|none|
|»»» numeroSerie|string|false|none|rang de l'ouvrage dans la série|2|none|none|none|
|»»» serieIssn|string|false|none|N° ISSN de la série|none|none|none|none|
|»» noticeId|integer(int64)|true|none|Identifiant de la notice chez Electre|0-5325984|none|none|none|
|»» isbns|[string]|false|none|International Standard Book Number|978-2-07-014432-7<br><br>Cas d'un article avec deux EAN : <br><br>978-2-330-12712-1<br>978-2-7609-1322-6|none|none|none|
|»» felCodeRetour|string|false|none|Code indiquant si cet article peut être ou non retourné.<br>- "retour-possible-selon-CGV" (code retour Dilicom 1)<br>- "retour-interdit" (code retour Dilicom 2)<br>- "retour-interdit-sauf-accord-cial" (code retour Dilicom 3)<br>- "retour-sur-couverture" (code retour Dilicom 5)<br>- "retour-sur-couverture-obligatoire" (code retour Dilicom 6)|3|none|none|none|
|»» eans|[string]|true|none|Identifiants EAN de l'ouvrage (plusieurs EAN possibles)|9782070144327<br>       <br>Cas d'un article avec deux EAN : <br><br>9782330127121<br>9782760913226|none|none|none|
|»» auteursPrincipaux|[object]|false|none|auteurs principaux de l'ouvrage|Ex : 9782070144327|none|none|none|
|»»» auteurId|string|true|none|identifiant de l'auteur|0-1254743|none|none|none|
|»»» nom|string|false|none|nom de l'auteur|Franz|none|none|none|
|»»» prenom|string|false|none|prénom de l'auteur|Kafka|none|none|none|
|»»» formebib|string|true|none|forme bibliographique du nom de l'auteur|Kafka, Franz|none|none|none|
|»»» typeContribution|string|true|none|Type de contribution principale (Auteur, Adaptateur, Producteur, etc.), <br>Enumerated values in: ["Auteur", "Auteur (photographe)", "Auteur (illustrateur)", "Interviewer", "Personne interviewée", "Auteur du texte", "Auteur originel", "Auteur adapté", "Adaptateur", "Auteur douteux, prétendu", "Auteur (artiste)", "Librettiste", "Parolier", "Compositeur", "Programmeur", "Infographiste", "Scénariste", "Dialoguiste", "Concepteur", "Producteur", "Réalisateur de film"]|Auteur (Auteur = libelle du code contribution A01)<br>Auteur (photographe = libellé du code contribution A11)|none|none|none|
|»»» nationalites|[object]|false|none|nationalités de l'auteur|Nationalité figurant sur le passeport<br>Tchèque, République, Grande-Breagne (et non pas Ecosse ou Pays de Galle)|none|none|none|
|»»» qualificatifs|[string]|false|none|date de naissance, date de mort, titre nobiliaire...|1883-1924|none|none|none|
|»»» idBNF|string|false|none|identifiant BNF de l'auteur|11909301|none|none|none|
|»» genres|[object]|false|none|Indexation genre de la base Electre|Ex : 9782070144327|none|none|none|
|»»» genreId|string|true|none|Code pour toute la branche|GLET001|none|none|none|
|»»» libelleGenre|string|true|none|Libellé de toute la branche|Littératures et textes étrangers classiques -- Traduction en français|none|none|none|
|»» felImpressionDemande|boolean|false|none|désigne les articles en impression à la demande. L'IAD est aussi un type de produit envoyé dans le champ "support"|Ex1 : 9782070144327 : Impression à la demande  = "false"<br><br>Ex2 : 9782010144097 : Impression à la demande  = "true"|none|none|none|
|»» prix|object|true|none|Prix de vente de l'ouvrage|Ex : 9782070144327|none|none|none|
|»»» devise|string|true|none|Code ISO de la devise|EUR|none|none|EUR|
|»»» taxes|[object]|false|none|Détail des taxes : TVA sur le livre (ou sur un autre type de produit si l'article comprend d'autres types de produits)|none|none|none|none|
|»»»» taxeId|string|true|none|Identifiant de la taxe (TVA)|TVA|none|none|none|
|»»»» horsTaxe|number(double)|true|none|Montant hors taxe sur lequel la taxe s'applique|56.87|0|-|none|
|»»»» tva|number(double)|true|none|Taux de taxe appliqué|5.5|none|none|none|
|»»» ttc|number(double)|true|none|Montant TTC|60.00|none|none|none|
|»» descriptionPhysique|object|false|none|caractéristiques physiques de l'article|Ex : 9782070144327|none|none|none|
|»»» nbPages|integer(int64)|false|none|nombre de pages|XXIV-1051|none|none|none|
|»»» largeur|number(double)|false|none|largeur de l'ouvrage, en centimètres|11|none|none|none|
|»»» hauteur|number(double)|false|none|hauteur de l'ouvrage, en centimètres|17|none|none|none|
|»»» epaisseur|number(double)|false|none|épaisseur de l'ouvrage, en centimètres|3.0|none|none|none|
|»»» mentionIllustrations|string|false|none|types d'illustrations (illustrations en couleur, en noir et blanc)|Ex : 9782203191143 : illustrations en couleur|none|none|none|
|»»» poids|integer(int64)|false|none|poids de l'ouvrage, en grammes|444|none|none|none|
|»»» reliure|string|false|none|type de reliure de l'ouvrage|Relié sous étui|none|none|none|
|»» flagFiction|boolean|false|none|Indique s'il s'agit d'un ouvrage de fiction ou non.|"true"<br><br>Ex article avec le flag fiction à "false" =  9782210167285|none|none|none|
|»» disponibilite|string|true|none|Disponibilité de l'ouvrage, Enumerated values in: [\"epuise\", \"manquan\t", \"a-paraitre\", \"disponible\"]|disponible<br><br>Autres valeurs possibles : <br><br>épuisé <br>à paraître <br>manquant|none|none|none|
|»» desactive|boolean|true|none|Indique si la notice a existée mais a été désactivée. Toujours à FALSE pour le endpoint /init, parfois à TRUE pour le endpoint /updated.|none|none|none|none|
|»» disponibiliteEtendue|object|true|none|Disponibilité de l'ouvrage, <br>Enumerated values in:<br> [\"epuise\", \"arret de commercialisation\", \"ne sera plus distribue\", \"reimpression en cours\", \"manque provisoirement\", \"a-paraitre\", \"disponible\"]|Valeurs possibles :<br><br>1 = disponible<br>2 = à paraître<br>3 = réimpression en cours<br>4 = manque provisoirement <br>5 = épuisé<br>6 = arrêt de commercialisation <br>7 = ne sera plus distribué<br>8 = à reparaitre|none|none|none|
|»»» disponibiliteEtendueId|integer(int64)|true|none|Valeur de disponibilité parmis 1,2 ,3 ,4, 5, 6, 7 ,8, 9<br>Mapping :<br>disponible                1<br>a-paraitre                 2<br>reimpression-en-cours      3<br>manque-provisoirement    4<br>epuise                     5<br>arret-de-commercialisation 6<br>ne-sera-plus-distribue     7<br>a-reparaitre               8<br>parution-annulee       9|1|none|none|none|
|»»» disponibiliteEtendueLibelle|string|true|none|Valeur de disponibilité parmis <br>- disponible <br>- a-paraitre <br>- reimpression-en-cours    <br>- manque-provisoirement <br>- epuise <br>- arret-de-commercialisation <br>- ne-sera-plus-distribue <br>- a-reparaitre <br>- parution-annulee|disponible|none|none|none|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
OAuth2 ( Scopes: read )
</aside>

