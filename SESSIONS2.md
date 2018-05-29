<!-- $size: 16:9 -->

<style>pre { font-size:0.65em!important; } </style>

<img src="./images/gallica.btv1b8600258f.f6.png" align="left" style="height:500px; margin:10px; opacity:0.8;" />

Les outils CapiTainS, l’édition numérique et l’exploitation des textes
===

Thibault Clérice
École Nationale des Chartes / Lyon 3
thibault.clerice@chartes.psl.eu
@ponteineptique (Twitter / Github)


--- 

# Session 2

## Objectifs 

- Mise en ligne d'un corpus dans un contexte d'intégration continue
- Découvrir Nemo Et Nautilus
- Configuration d'une application Nemo/Nautilus
- Mise en ligne de l'application sur Heroku (Gratuit)

---

# L'intégration continue

**Principe:** L'intégration continue sert entre autres à lancer une batterie de tests développés par l'équipe de développement ou à compiler des logiciels à chaque modification sur un serveur centralisé.

**Pratique:** 
- Création d'un repository *git* sur GitHub ( http://github.com )
- Connexion du repository sur TravisCI ( http://travis-ci.org/ )
- Configuration du fichier `.travis.yml`

---

# Un script travis Hooktest basique

```yml
filter_secrets: false
language: python
python:
  - "3.5"

install:
  - pip3 install HookTest>=1.0.0

script:
  - hooktest ./ --scheme tei --workers 3 --verbose 10 --console table --countword --allowfailure

```

---

# Nemo et Nautilus

## Nemo

Nemo est un squelette qui permet de créer une application basée sur les APIs supportées par Capitains. 

https://github.com/Capitains/flask-capitains-nemo
https://github.com/Capitains/tutorial-nemo

## Nautilus

Nautilus contient à la fois un *"parser"* des guidelines capitains optimisé pour le web (gestion du cache), et une application web pour créer une API (avec une configuration très légère).
https://github.com/capitains/Nautilus

---

# Nemo + Nautilus

Les deux applications sont complètement indépendantes : l'une marche sans l'autre. Mais c'est sans doute en combinant les deux qu'elles intéresseront le plus de personnes. 

https://github.com/capitains/nemo-template-app

---

# Mise en ligne

Vous-même ou votre administration réseau
- Apache + uWSGI : http://flask.pocoo.org/docs/0.12/deploying/mod_wsgi/
- NGINX + Gunicorn : https://medium.com/ymedialabs-innovation/deploy-flask-app-with-nginx-using-gunicorn-and-supervisor-d7a93aa07c18
- Heroku : https://github.com/Capitains/tutorial-nemo/blob/master/6-setting-up-heroku.md 
- Bonus : [Raspberry PI](https://www.techcoil.com/blog/how-to-deploy-python-3-flask-application-on-raspberry-pi-3-with-raspbian-stretch-lite-nginx-supervisor-virtualenv-and-gunicorn/)

Une infrastructure française ?
- HumaNum