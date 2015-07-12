# Intro

Zenika était à l'espace Charenton à Paris pour la deuxième conférence React après la ReactJS.conf en janvier : React-europe. Une partie de la core team React (mais aussi Relay / GraphQL) était présente pour nous parler des nouveautés des 6 derniers mois ainsi que les directions prises dans le futur.

## TL:DR;
Deux notions sont revenues dans beaucoup de talks et ont donné l'esprit général du contenu de la conférence :
- La DX (Developer eXperience): aussi importante de l'UX, elle est au coeur des librairies de l'écosytème React. Le futur des animations en React par exemple est tourné vers la DX.
- React doit être vu comme un principe, une philosophie. Le React actuel est une implémentation (DOM), React Native en est une autre (iOS). Ce détachement était un thèmme récurrent: React dans le canvas, React comme aggrégateur de données coté serveur, React dans le terminal (WTF ?),... Sebastian Markbage allant même jusqu'à présenter une charge contre le DOM qu'il présente comme un boulet accroché au pied de React. Ce détachement est d'ailleurs la nouveauté de la version 0.14 dont la beta a été annoncé dans un [blog post](https://facebook.github.io/react/blog/2015/07/03/react-v0.14-beta-1.html) durant la conférence.


## Keynote

La keynote était présentée par Christopher Chedeau (@vjeux), le *frenchie* de la team React, qui était également le chef d'orchestre de la conférence. L'évolution de l'écosystème React est comparable à la méthode du [Recuit simulé]() procédé industriel s'appuyant sur un refroidissement maîtrisé d'un matériau transitant petit à petit d'un état instable où les atomes fusent dans tous les sens vers un état stable où les molécules se forment et s'ordonnent pour former un matériau solide et fiable. React est dans cet état transitoire : certains concepts ont évolués, d'autres ont disparu, d'autres encore sont devenus incontournables (immutabilité, compilation avec Babel, build avec Webpack + react-hot-loader) : d'après Christopher, nous tendons de plus en plus vers un écosystème stable et performant, le React de demain.

Déjà quelques annonces sur la keynote avec une disponibilité de React-native pour Android prévue pour début octobre (TODO Verif). En guise de teasing, Christopher a évoqué un portage d'une app mobile React-Native iOS vers Android où **87%** du code a pu être réutilisé !

Pour conclure la keynote, Christopher nous assure que l'empreinte de Facebook est de plus en plus réduite, les contributeurs open-source sont plus que jamais les bienvenus, en s'osant même un brin moralisateur sur la "concurrence malsaine" introduite par les différentes communautés (Angular, Ember, Backbone, ...). Le mot d'ordre est "Aimez vous les uns les autres" et "Do not feed the troll" !

## Inline styles

Comme abordé dans un précédent article, les CSS sont un peu le parent pauvre des applications React. Le JSX impose de mixer la logique impérative de la page avec sa structure HTML, améliorant ainsi la DX (plus besoin de naviguer sans cesse entre le template et le script !). Faire la même chose en CSS revient finalement à faire du style "inline" dans le composant, mais le cap est alors plus difficile à franchir. Michael Chan (@chantastic) nous explique là le bienfondé de cette pratique, mais surtout les incongruïtés de l'état de l'art ("bullshit", a t'on cru entendre !).

### Style is not CSS

Par abus de langage, "les styles" et "la CSS" désignent la même chose, mais n'oublions pas que la CSS n'est qu'une façon de déclarer les styles de notre application. A l'origine, les styles étaient déclarés dans l'attribut `style`, avec les problèmes de duplication et de lisibilité que l'on connait. Les sélecteurs CSS et le web sémantique (balises h1, h2, p, ul, li, ...) ont permit l'externalisation des styles dans une CSS. Michael souligne qu'avec `h1 {font-weight: bold;}` d'un coté et `<div class=menu">...</div>` le HTML et le CSS sont déjà intimement lié.






