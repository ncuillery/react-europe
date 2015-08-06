# Live React: Hot Reloading With Time Travel

Dan Abramov, talentueux contributeur open-source, présente ses 2 projets majeurs : [react-hot-loader](https://github.com/gaearon/react-hot-loader) et [redux](https://github.com/gaearon/redux). Ces 2 projets sont nés de la frustration engendré par le développement Web. 

## react-hot-loader

La frustation qui a conduit à la création de react-hot-loader est évidente: c'est le workflow standard de développement d'une application web:
- Modification d'une portion de code
- Build
- Actualisation du navigateur
- Recherche de l'état d'origine (navigation, saisie, etc.)
- Retour au premier point...

Que de temps perdu à chacune de ces étapes ! C'est là qu'intervient react-hot-loader, un module pour webpack. A l'aide une courte démo, Dan nous montre la modification à chaud d'un composant React, aussi bien cosmétique que logique.

Ensuite vient l'explication technique, on comprend que le hot-reload est rendue possible par les fonctionnalités conjugués de 3 briques:
- Webpack, qui permet le remplacement à chaud de n'importe quel module CommonJS ([HMR](http://webpack.github.io/docs/hot-module-replacement.html)),
- react-hot-loader, qui intervient en cas de modification de composant React, il agit comme un **proxy** sur les méthodes du composant : en cas de modification d'une méthode (`render`, `componentDidMount`, etc.), l'ancienne méthode proxyfiée est remplacée par la nouvelle. Ainsi, l'état du composant est préservé. 
- React lui-même, qui propose une fonction de rendu [pure](https://fr.wikipedia.org/wiki/Fonction_pure) : le `render` ne dépend que des propriétés en entrée (props / state). De fait, le remplacement de cette fonction par react-hot-loader permet à lui seul d'obtenir le nouveau rendu.

## La sérendipité de Redux

Là encore, c'est la frustation né de l'écriture des stores dans une application Flux qui a poussé Dan à réfléchir à une simplification et à finalement écrire complètement une nouvelle implémentation Flux:
https://twitter.com/dan_abramov/status/604356871722569728

Les stores sont trop compliqués. Première étape, la notification : partant du principe que les [stores doivent être immutables](https://facebook.github.io/react/docs/advanced-performance.html#immutable-js-and-flux), la simple comparaison de référence permet de savoir si l'état du store a changé, rendant le principe de notification des stores inutiles.

Ensuite, l'étape d'enregistrement du store auprès du dispatcher est inutile : l'existence d'un store suffit à elle-même pour indiquer que le dispatcher doit s'en préoccuper !

Enfin, Redux va tordre le cou aux getters que l'on définit dans les stores pour accéder aux données. Selon Dan, ce n'est pas le rôle du store de définir la logique d'accès aux données. Son rôle est de les stocker: c'est **l'état** du store que les handlers vont recevoir en paramètre, en modifier les références et le retourner.

Ainsi, on peut schématiser le fonctionnement des stores comme suit: 
```
(state, action) => state
```
Le store recoit le state courant + une action et renvoit le nouveau state. Cette "signature" ressemble fortement à
```
(accumulator, value) => accumulator
```
C'est la signature d'un reduce ! L'exécution d'une action peut donc être vue comme une opération de reduce, à qui on passerait le state courant et de qui on récupérerait le nouveau state, d'où le nom Redux (contraction de Reduce + Flux).

Via une impressionnante démo, Dan nous montre qu'à travers un simple composant de debug, on peut observer la liste des modifications du store occasionnées par la navigation de l'utilisateur. On peut revenir en arrière, la rejouer (à l'identique ou pas), etc.

## Ma conclusion

Il le dit lui-même, Dan n'a jamais eu l'occasion de s'expliquer sur ce qui l'a poussé à créer Redux, il le fait aujourd'hui avec talent. L'explication est claire et nous pousse à croire en Redux, malgré les libertés prises sur le pattern. C'est l'implémentation Flux la plus "hype" à l'heure où j'écris ces lignes. 

Les démos sont efficaces et convainquent également de l'intérêt d'un bon outillage. On se rapproche bien de la thématique DX (Developer eXperience).

https://twitter.com/E0M/status/616605333964730369
