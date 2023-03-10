# Getting existing entries

Documentation for this method:

https://app.wallabag.it/api/doc#get--api-entries.{_format}

As we work on a fresh wallabag installation, we'll have no result with this command:

```bash
http GET http://localhost:8000/api/entries.json \
"Authorization:Bearer ZGJmNTA2MDdmYTdmNWFiZjcxOWY3MWYyYzkyZDdlNWIzOTU4NWY3NTU1MDFjOTdhMTk2MGI3YjY1ZmI2NzM5MA"
```

returns:

```http
HTTP/1.1 200 OK
0: application/json
Cache-Control: no-cache
Connection: close
Content-Type: application/json
Date: Tue, 05 Apr 2016 08:51:32 GMT
Host: localhost:8000
Set-Cookie: PHPSESSID=nrogm748md610ovhu6j70c3q63; path=/; HttpOnly
X-Debug-Token: 4fbbc4
X-Debug-Token-Link: /_profiler/4fbbc4
X-Powered-By: PHP/7.0.4

{
    "_embedded": {
        "items": []
    },
    "_links": {
        "first": {
            "href": "http://localhost:8000/api/entries?page=1&perPage=30"
        },
        "last": {
            "href": "http://localhost:8000/api/entries?page=1&perPage=30"
        },
        "self": {
            "href": "http://localhost:8000/api/entries?page=1&perPage=30"
        }
    },
    "limit": 30,
    "page": 1,
    "pages": 1,
    "total": 0
}
```

The `items` array is empty.

cURL example:

```bash
curl --get "https://localhost:8000/api/entries.html?access_token=ZGJmNTA2MDdmYTdmNWFiZjcxOWY3MWYyYzkyZDdlNWIzOTU4NWY3NTU1MDFjOTdhMTk2MGI3YjY1ZmI2NzM5MA"
```

# Adding your first entry

Documentation for this method: https://app.wallabag.it/api/doc#post--api-entries.{_format}

```bash
http POST http://localhost:8000/api/entries.json \
"Authorization:Bearer ZGJmNTA2MDdmYTdmNWFiZjcxOWY3MWYyYzkyZDdlNWIzOTU4NWY3NTU1MDFjOTdhMTk2MGI3YjY1ZmI2NzM5MA" \
url="http://www.numerama.com/tech/160115-le-pocket-libre-wallabag-fait-le-plein-de-fonctionnalites.html"
```

returns

```http
HTTP/1.1 200 OK
0: application/json
Cache-Control: no-cache
Connection: close
Content-Type: application/json
Date: Tue, 05 Apr 2016 09:07:54 GMT
Host: localhost:8000
Set-Cookie: PHPSESSID=bjie40ck72kp2pst3i71gf43a4; path=/; HttpOnly
X-Debug-Token: e01c51
X-Debug-Token-Link: /_profiler/e01c51
X-Powered-By: PHP/7.0.4

{
    "_links": {
        "self": {
            "href": "/api/entries/1"
        }
    },
    "content": "<p class=\"chapo\">Fonctionnant sur le m??me principe que Pocket, Instapaper ou Readability, le logiciel Wallabag permet de m??moriser des articles pour les lire plus tard. Sa nouvelle version apporte une multitude de nouvelles fonctionnalit??s.</p><p>Si vous utilisez Firefox comme navigateur web, vous avez peut-??tre constat?? l???arriv??e d???<a href=\"http://www.numerama.com/magazine/33292-update-firefox.html\">une fonctionnalit?? intitul??e Pocket</a>. Disponible autrefois sous la forme d???un module compl??mentaire, et sous un autre nom (Read it Later), elle est depuis le mois de juin 2015 directement incluse au sein de Firefox.</p>\n<p>Concr??tement, Pocket sert ?? garder en m??moire des contenus que vous croisez au fil de la navigation, comme des articles de presse ou des vid??os, afin de pouvoir les consulter plus tard. Pocket fonctionne un peu comme un syst??me de favoris, mais en bien plus ??labor?? gr??ce ?? ses options suppl??mentaires.</p>\n<p>Mais <a href=\"https://en.wikipedia.org/wiki/Pocket_%28application%29#Firefox_integration\" target=\"_blank\">Pocket fait pol??mique</a>, car il s???agit d???un projet propri??taire qui est int??gr?? dans un logiciel libre. C???est pour cette raison que des utilisateurs ont choisi de se tourner vers d???autres solutions, comme <strong>Wallabag</strong>, qui est l?????quivalent libre de Pocket et d???autres syst??mes du m??me genre, comme Instapaper et Readability.</p>\n<p>Et justement, Wallabag ??volue. C???est ce dimanche que la <a href=\"https://www.wallabag.org/blog/2016/04/03/wallabag-v2\" target=\"_blank\">version 2.0.0 du logiciel</a> a ??t?? publi??e par l?????quipe en?? charge de son d??veloppement et celle-ci contient de nombreux changements par rapport aux moutures pr??c??dentes (la <a href=\"http://doc.wallabag.org/fr/v2/\" target=\"_blank\">documentation est traduite</a> en fran??ais), lui permettant d???appara??tre comme une alternative ?? Pocket, Instapaper et Readability.</p>\n<p><img class=\"aligncenter size-medium wp-image-160439\" src=\"http://www.numerama.com/content/uploads/2016/04/homepage-680x347.png\" alt=\"homepage\" width=\"680\" height=\"347\" srcset=\"//www.numerama.com/content/uploads/2016/04/homepage-680x347.png 680w, //www.numerama.com/content/uploads/2016/04/homepage-1024x523.png 1024w, //www.numerama.com/content/uploads/2016/04/homepage-270x138.png 270w, //www.numerama.com/content/uploads/2016/04/homepage.png 1286w\" sizes=\"(max-width: 680px) 100vw, 680px\"/></p>\n<p>Parmi les principaux changements que l???on peut retenir avec cette nouvelle version, notons la possibilit?? d?????crire des annotations dans les articles m??moris??s, de filtrer les contenus selon divers crit??res (temps de lecture, nom de domaine, date de cr??ation, statut???), d???assigner des mots-cl??s aux entr??es, de modifier le titre des articles, le support des flux RSS ou encore le support de plusieurs langues dont le fran??ais.</p>\n<p>D???autres options sont ??galement ?? signaler, comme l???aper??u d???un article m??moris?? (si l???option est disponible), un guide de d??marrage rapide pour les d??butants, un outil d???export dans divers formats (PDF, JSON, EPUB, MOBI, XML, CSV et TXT) et, surtout, la possibilit?? de migrer vers Wallabag depuis Pocket, afin de convaincre les usagers de se lancer.</p>\n    \n    \n    <footer class=\"clearfix\" readability=\"1\"><p class=\"source\">\n        Cr??dit photo de la une : <a href=\"https://www.flickr.com/photos/bookgrl/2388310523/\">Laura Taylor</a>\n    </p>\n    \n    <p><a href=\"http://www.numerama.com/tech/160115-le-pocket-libre-wallabag-fait-le-plein-de-fonctionnalites.html?&amp;show_reader_reports\" target=\"_blank\" rel=\"nofollow\">Signaler une erreur dans le texte</a></p>\n        \n</footer>    <section class=\"related-article\"><header><h3>Articles li??s</h3>\n    </header><article class=\"post-grid format-article\"><a class=\"floatleft\" href=\"http://www.numerama.com/magazine/34444-firefox-prepare-l-enterrement-des-vieux-plugins.html\" title=\"Firefox pr??pare l'enterrement des vieux plugins\">\n        <div class=\"cover-preview cover-tech\">\n                            <p>Lire</p>\n            \n                            \n            \n            <img class=\"cover-preview_img\" src=\"http://c2.lestechnophiles.com/www.numerama.com/content/uploads/2015/10/cimetierecolleville.jpg?resize=200,135\" srcset=\"&#10;                    //c2.lestechnophiles.com/www.numerama.com/content/uploads/2015/10/cimetierecolleville.jpg?resize=200,135 200w,&#10;                                            //c2.lestechnophiles.com/www.numerama.com/content/uploads/2015/10/cimetierecolleville.jpg?resize=100,67 100w,&#10;                                        \" sizes=\"(min-width: 1001px) 200px, (max-width: 1000px) 100px\" alt=\"Firefox pr??pare l'enterrement des vieux plugins\"/></div>\n        <h4> Firefox pr??pare l'enterrement des vieux plugins </h4>\n    </a>\n    <footer class=\"span12\">\n    </footer></article><article class=\"post-grid format-article\"><a class=\"floatleft\" href=\"http://www.numerama.com/tech/131636-activer-navigation-privee-navigateur-web.html\" title=\"Comment activer la navigation priv??e sur son navigateur web\">\n        <div class=\"cover-preview cover-tech\">\n                            <p>Lire</p>\n            \n                            \n            \n            <img class=\"cover-preview_img\" src=\"http://c1.lestechnophiles.com/www.numerama.com/content/uploads/2015/11/Incognito.jpg?resize=200,135\" srcset=\"&#10;                    //c1.lestechnophiles.com/www.numerama.com/content/uploads/2015/11/Incognito.jpg?resize=200,135 200w,&#10;                                            //c1.lestechnophiles.com/www.numerama.com/content/uploads/2015/11/Incognito.jpg?resize=100,67 100w,&#10;                                        \" sizes=\"(min-width: 1001px) 200px, (max-width: 1000px) 100px\" alt=\"Comment activer la navigation priv??e sur son navigateur web\"/></div>\n        <h4> Comment activer la navigation priv??e sur son navigateur web </h4>\n    </a>\n    <footer class=\"span12\">\n    </footer></article><article class=\"post-grid format-article\"><a class=\"floatleft\" href=\"http://www.numerama.com/tech/144028-firefox-se-mettra-a-jour-regulierement.html\" title=\"Firefox se mettra ?? jour un peu moins r??guli??rement\">\n        <div class=\"cover-preview cover-tech\">\n                            <p>Lire</p>\n            \n                            \n            \n            <img class=\"cover-preview_img\" src=\"http://c0.lestechnophiles.com/www.numerama.com/content/uploads/2016/02/firefox-mobile.jpg?resize=200,135\" srcset=\"&#10;                    //c0.lestechnophiles.com/www.numerama.com/content/uploads/2016/02/firefox-mobile.jpg?resize=200,135 200w,&#10;                                            //c0.lestechnophiles.com/www.numerama.com/content/uploads/2016/02/firefox-mobile.jpg?resize=100,67 100w,&#10;                                        \" sizes=\"(min-width: 1001px) 200px, (max-width: 1000px) 100px\" alt=\"Firefox se mettra ?? jour un peu moins r??guli??rement\"/></div>\n        <h4> Firefox se mettra ?? jour un peu moins r??guli??rement </h4>\n    </a>\n    <footer class=\"span12\">\n    </footer></article>\n</section>\n",
    "created_at": "2016-04-05T09:07:54+0000",
    "domain_name": "www.numerama.com",
    "id": 1,
    "is_archived": 0,
    "is_starred": 0,
    "language": "fr-FR",
    "mimetype": "text/html",
    "preview_picture": "http://www.numerama.com/content/uploads/2016/04/post-it.jpg",
    "reading_time": 2,
    "tags": [],
    "title": "Le Pocket libre Wallabag fait le plein de fonctionnalit??s - Tech - Numerama",
    "updated_at": "2016-04-05T09:07:54+0000",
    "url": "http://www.numerama.com/tech/160115-le-pocket-libre-wallabag-fait-le-plein-de-fonctionnalites.html",
    "user_email": "",
    "user_id": 1,
    "user_name": "wallabag"
}
```

Now, if you execute the previous command (see **Get existing entries**), you'll have data.

cURL example:

```bash
curl "https://localhost:8000/api/entries.html?access_token=ZGJmNTA2MDdmYTdmNWFiZjcxOWY3MWYyYzkyZDdlNWIzOTU4NWY3NTU1MDFjOTdhMTk2MGI3YjY1ZmI2NzM5MA&url=http://www.numerama.com/tech/160115-le-pocket-libre-wallabag-fait-le-plein-de-fonctionnalites.html"
```

# Deleting an entry

Documentation for this method: https://app.wallabag.it/api/doc#delete--api-entries-{entry}.{_format}

```bash
http DELETE http://localhost:8000/api/entries/1.json \
"Authorization:Bearer ZGJmNTA2MDdmYTdmNWFiZjcxOWY3MWYyYzkyZDdlNWIzOTU4NWY3NTU1MDFjOTdhMTk2MGI3YjY1ZmI2NzM5MA"
```

returns

```http
HTTP/1.1 200 OK
0: application/json
Cache-Control: no-cache
Connection: close
Content-Type: application/json
Date: Tue, 05 Apr 2016 09:19:07 GMT
Host: localhost:8000
Set-Cookie: PHPSESSID=jopgnfvmuc9a62b27sqm6iulr6; path=/; HttpOnly
X-Debug-Token: 887cef
X-Debug-Token-Link: /_profiler/887cef
X-Powered-By: PHP/7.0.4

{
    "_links": {
        "self": {
            "href": "/api/entries/"
        }
    },
    "annotations": [],
    "content": "<p class=\"chapo\">Fonctionnant sur le m??me principe que Pocket, Instapaper ou Readability, le logiciel Wallabag permet de m??moriser des articles pour les lire plus tard. Sa nouvelle version apporte une multitude de nouvelles fonctionnalit??s.</p><p>Si vous utilisez Firefox comme navigateur web, vous avez peut-??tre constat?? l???arriv??e d???<a href=\"http://www.numerama.com/magazine/33292-update-firefox.html\">une fonctionnalit?? intitul??e Pocket</a>. Disponible autrefois sous la forme d???un module compl??mentaire, et sous un autre nom (Read it Later), elle est depuis le mois de juin 2015 directement incluse au sein de Firefox.</p>\n<p>Concr??tement, Pocket sert ?? garder en m??moire des contenus que vous croisez au fil de la navigation, comme des articles de presse ou des vid??os, afin de pouvoir les consulter plus tard. Pocket fonctionne un peu comme un syst??me de favoris, mais en bien plus ??labor?? gr??ce ?? ses options suppl??mentaires.</p>\n<p>Mais <a href=\"https://en.wikipedia.org/wiki/Pocket_%28application%29#Firefox_integration\" target=\"_blank\">Pocket fait pol??mique</a>, car il s???agit d???un projet propri??taire qui est int??gr?? dans un logiciel libre. C???est pour cette raison que des utilisateurs ont choisi de se tourner vers d???autres solutions, comme <strong>Wallabag</strong>, qui est l?????quivalent libre de Pocket et d???autres syst??mes du m??me genre, comme Instapaper et Readability.</p>\n<p>Et justement, Wallabag ??volue. C???est ce dimanche que la <a href=\"https://www.wallabag.org/blog/2016/04/03/wallabag-v2\" target=\"_blank\">version 2.0.0 du logiciel</a> a ??t?? publi??e par l?????quipe en?? charge de son d??veloppement et celle-ci contient de nombreux changements par rapport aux moutures pr??c??dentes (la <a href=\"http://doc.wallabag.org/fr/v2/\" target=\"_blank\">documentation est traduite</a> en fran??ais), lui permettant d???appara??tre comme une alternative ?? Pocket, Instapaper et Readability.</p>\n<p><img class=\"aligncenter size-medium wp-image-160439\" src=\"http://www.numerama.com/content/uploads/2016/04/homepage-680x347.png\" alt=\"homepage\" width=\"680\" height=\"347\" srcset=\"//www.numerama.com/content/uploads/2016/04/homepage-680x347.png 680w, //www.numerama.com/content/uploads/2016/04/homepage-1024x523.png 1024w, //www.numerama.com/content/uploads/2016/04/homepage-270x138.png 270w, //www.numerama.com/content/uploads/2016/04/homepage.png 1286w\" sizes=\"(max-width: 680px) 100vw, 680px\"/></p>\n<p>Parmi les principaux changements que l???on peut retenir avec cette nouvelle version, notons la possibilit?? d?????crire des annotations dans les articles m??moris??s, de filtrer les contenus selon divers crit??res (temps de lecture, nom de domaine, date de cr??ation, statut???), d???assigner des mots-cl??s aux entr??es, de modifier le titre des articles, le support des flux RSS ou encore le support de plusieurs langues dont le fran??ais.</p>\n<p>D???autres options sont ??galement ?? signaler, comme l???aper??u d???un article m??moris?? (si l???option est disponible), un guide de d??marrage rapide pour les d??butants, un outil d???export dans divers formats (PDF, JSON, EPUB, MOBI, XML, CSV et TXT) et, surtout, la possibilit?? de migrer vers Wallabag depuis Pocket, afin de convaincre les usagers de se lancer.</p>\n    \n    \n    <footer class=\"clearfix\" readability=\"1\"><p class=\"source\">\n        Cr??dit photo de la une : <a href=\"https://www.flickr.com/photos/bookgrl/2388310523/\">Laura Taylor</a>\n    </p>\n    \n    <p><a href=\"http://www.numerama.com/tech/160115-le-pocket-libre-wallabag-fait-le-plein-de-fonctionnalites.html?&amp;show_reader_reports\" target=\"_blank\" rel=\"nofollow\">Signaler une erreur dans le texte</a></p>\n        \n</footer>    <section class=\"related-article\"><header><h3>Articles li??s</h3>\n    </header><article class=\"post-grid format-article\"><a class=\"floatleft\" href=\"http://www.numerama.com/magazine/34444-firefox-prepare-l-enterrement-des-vieux-plugins.html\" title=\"Firefox pr??pare l'enterrement des vieux plugins\">\n        <div class=\"cover-preview cover-tech\">\n                            <p>Lire</p>\n            \n                            \n            \n            <img class=\"cover-preview_img\" src=\"http://c2.lestechnophiles.com/www.numerama.com/content/uploads/2015/10/cimetierecolleville.jpg?resize=200,135\" srcset=\"&#10;                    //c2.lestechnophiles.com/www.numerama.com/content/uploads/2015/10/cimetierecolleville.jpg?resize=200,135 200w,&#10;                                            //c2.lestechnophiles.com/www.numerama.com/content/uploads/2015/10/cimetierecolleville.jpg?resize=100,67 100w,&#10;                                        \" sizes=\"(min-width: 1001px) 200px, (max-width: 1000px) 100px\" alt=\"Firefox pr??pare l'enterrement des vieux plugins\"/></div>\n        <h4> Firefox pr??pare l'enterrement des vieux plugins </h4>\n    </a>\n    <footer class=\"span12\">\n    </footer></article><article class=\"post-grid format-article\"><a class=\"floatleft\" href=\"http://www.numerama.com/tech/131636-activer-navigation-privee-navigateur-web.html\" title=\"Comment activer la navigation priv??e sur son navigateur web\">\n        <div class=\"cover-preview cover-tech\">\n                            <p>Lire</p>\n            \n                            \n            \n            <img class=\"cover-preview_img\" src=\"http://c1.lestechnophiles.com/www.numerama.com/content/uploads/2015/11/Incognito.jpg?resize=200,135\" srcset=\"&#10;                    //c1.lestechnophiles.com/www.numerama.com/content/uploads/2015/11/Incognito.jpg?resize=200,135 200w,&#10;                                            //c1.lestechnophiles.com/www.numerama.com/content/uploads/2015/11/Incognito.jpg?resize=100,67 100w,&#10;                                        \" sizes=\"(min-width: 1001px) 200px, (max-width: 1000px) 100px\" alt=\"Comment activer la navigation priv??e sur son navigateur web\"/></div>\n        <h4> Comment activer la navigation priv??e sur son navigateur web </h4>\n    </a>\n    <footer class=\"span12\">\n    </footer></article><article class=\"post-grid format-article\"><a class=\"floatleft\" href=\"http://www.numerama.com/tech/144028-firefox-se-mettra-a-jour-regulierement.html\" title=\"Firefox se mettra ?? jour un peu moins r??guli??rement\">\n        <div class=\"cover-preview cover-tech\">\n                            <p>Lire</p>\n            \n                            \n            \n            <img class=\"cover-preview_img\" src=\"http://c0.lestechnophiles.com/www.numerama.com/content/uploads/2016/02/firefox-mobile.jpg?resize=200,135\" srcset=\"&#10;                    //c0.lestechnophiles.com/www.numerama.com/content/uploads/2016/02/firefox-mobile.jpg?resize=200,135 200w,&#10;                                            //c0.lestechnophiles.com/www.numerama.com/content/uploads/2016/02/firefox-mobile.jpg?resize=100,67 100w,&#10;                                        \" sizes=\"(min-width: 1001px) 200px, (max-width: 1000px) 100px\" alt=\"Firefox se mettra ?? jour un peu moins r??guli??rement\"/></div>\n        <h4> Firefox se mettra ?? jour un peu moins r??guli??rement </h4>\n    </a>\n    <footer class=\"span12\">\n    </footer></article>\n</section>\n",
    "created_at": "2016-04-05T09:07:54+0000",
    "domain_name": "www.numerama.com",
    "is_archived": 0,
    "is_starred": 0,
    "language": "fr-FR",
    "mimetype": "text/html",
    "preview_picture": "http://www.numerama.com/content/uploads/2016/04/post-it.jpg",
    "reading_time": 2,
    "tags": [],
    "title": "Le Pocket libre Wallabag fait le plein de fonctionnalit??s - Tech - Numerama",
    "updated_at": "2016-04-05T09:07:54+0000",
    "url": "http://www.numerama.com/tech/160115-le-pocket-libre-wallabag-fait-le-plein-de-fonctionnalites.html",
    "user_email": "",
    "user_id": 1,
    "user_name": "wallabag"
}
```

And if you want to list the existing entries (see **Get existing entries**), the array is empty.

cURL example:

```bash
curl --request DELETE "https://localhost:8000/api/entries/1.html?access_token=ZGJmNTA2MDdmYTdmNWFiZjcxOWY3MWYyYzkyZDdlNWIzOTU4NWY3NTU1MDFjOTdhMTk2MGI3YjY1ZmI2NzM5MA"
```

# Other methods

We didn't write samples for each API method.

Have a look on the listing here: https://app.wallabag.it/api/doc to know each method.
