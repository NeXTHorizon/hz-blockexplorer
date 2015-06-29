The assets function was contributed by altsheets. Do keep the credits:
/views/templates/altsheetsCredits.html  included the page
/views/templates/asset.phtml Thanks!

# HZ asset block explorer page
The [HZ blockexplorer](https://explorer.horizonplatform.io) ([orig source](https://github.com/pharesim/hz-blockexplorer)) was lacking a dedicated page for each asset, so I forked it into https://github.com/altsheets/hz-blockexplorer, and added that function. Please check my code, then pull it upstream.

Main aspects:
* table with all properties from getAsset
* if issuer 'account' has an 'alias', show it
* 'quantity' derived from 'quantityQNT' and 'decimals'
* hyperlink to the transaction in which the asset was issued (for date, etc.)
* use of colors for fast grokking

Made sense so I built it:
* 'numberOfTransfers' and numberOfAccounts' already implemented, for future HZ version.
* if 'asset id' is unknown, hide most of the table, only show the error message. 
* specific assets can display different warnings (see below).

## examples
* webpage proper asset http://188.226.155.38:8080/hzbe/?page=asset&id=8101260088962758269
* webpage wrong asset id http://188.226.155.38:8080/hzbe/?page=asset&id=0
* json api proper asset http://188.226.155.38:8080/hzbe/api.php?page=asset&id=8101260088962758269

## warnings
Some assets are known to be **test assets**, or **revoked**, or even **scams** (perhaps, probably or proven scams). 

However, the (too!) centralized power of the only official block explorer ... needs a balance between user and issuer protection! (Censorship is bad). So *all assets are still shown* - but in some cases with a clear warning.

All is hardcoded into an XML file. I urge the team to always link to a forum post where detailed explanations are given, and can be discussed - so that the issuer gets a chance to react to the suspicion.  

examples:
* test asset http://188.226.155.38:8080/hzbe/?page=asset&id=5903523947573024709
* revoked asset  http://188.226.155.38:8080/hzbe/?page=asset&id=16661902544444460183
* perhaps scam http://188.226.155.38:8080/hzbe/?page=asset&id=3
* probably scam http://188.226.155.38:8080/hzbe/?page=asset&id=4
* proven scam http://188.226.155.38:8080/hzbe/?page=asset&id=5

## affected files
In comparison to the [original block explorer](https://github.com/pharesim/hz-blockexplorer) I have changed or added at least these files [in my fork](https://github.com/altsheets/hz-blockexplorer): 

* assetsReadme.md (this readme here)
* todo.txt (some problems in the existing code that I noticed)

* classes/controller.php
* classes/model.php
* config/config.php

* views/templates/asset.phtml

* views/api/templates/asset.phtml
* views/api/templates/home.phtml

* views/cli/templates/asset.phtml (untested, I did not know how)

* data/assetwarnings.xml (hardcoded warnings for certain assets)

* prepareServer.sh (very useful if you want to install this to your own server!)

... perhaps even more. Check the commits on https://github.com/altsheets/hz-blockexplorer .

## license
Please pull upstream into the official block explorer - that's why I have built it.
But please (a) keep my credits in, and (b) consider to send me big bounty for this work. 

### temporary notes
When this is pulled upstream, replace all above 188.226.155.38:8080 with the official HZ blockexplorer domain. Then delete this note.
