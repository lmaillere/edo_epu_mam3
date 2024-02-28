# Installation de Julia

La façon la plus simple d'installer `Julia` est d'utiliser [juliaup](https://github.com/JuliaLang/juliaup).

Sur Linux, installez `curl` sur votre système (`sudo apt install curl` sur Ubuntu). Puis dans un terminal :
```bash
curl -fsSL https://install.julialang.org | sh
```
et procédez à l'installation.

Fermez et réouvrez votre terminal (ou rechargez votre fichier de préférences comme vous l'indique l'installateur de juliaup) pour pouvoir exécuter `Julia`.

Puis, si vous souhaitez utiliser `Julia` dans un notebook `jupyter`, installez le package `IJulia` depuis Julia comme suit (si le profil utilisateur linux est tout nouvellement, créé un redémarrage peut s'avérer nécessaire si vous rencontrez une erreur à l'exécution de `jupyterlab()` ci-dessous):
```
julia # executer julia dans un terminal
   _       _ _(_)_     |  Documentation: https://docs.julialang.org
  (_)     | (_) (_)    |
   _ _   _| |_  __ _   |  Type "?" for help, "]?" for Pkg help.
  | | | | | | |/ _` |  |
  | | |_| | | | (_| |  |  Version 1.10.0 (2023-12-25)
 _/ |\__'_|_|_|\__'_|  |  Official https://julialang.org/ release
|__/                   |

julia> ]  # package mode
(@v1.10) pkg> add IJulia
(@v1.10) pkg> build IJulia
```

La première commande `add IJulia` peut prendre un peu de temps.

Si vous avez déjà `jupyterlab` installé, un noyau `Julia` est ensuite disponible. Sinon vous pouvez l'installer et le démarrer directement depuis Julia :
```julia
julia> using IJulia # tapez backspace d'abord
                    # pour sortir du package mode
julia> jupyterlab()
```

Julia vous propose alors d'installer jupyterlab via miniconda, ce que vous accepterez, et démarre ensuite jupyterlab dans votre navigateur.

## utiliser un environnement

Pour télécharger les packages additionnels utilisés dans ce dépot, nous allons nous baser sur l'environnement défini dans les fichiers `Projet.toml` et `Manifest.toml`.

Clonez le dépot (e.g. dans un terminal):
```bash
git clone https://github.com/lmaillere/edo_epu_mam3.git
```
(ou téléchargez l'archive compressée et décompressez la sur votre ordinateur).

Ouvrez un terminal, positionnez vous dans le répertoire correspondant et démarrez Julia:
```julia
julia

julia> ]  # package mode
(@v1.10) pkg>
```

Puis nous activons, et "instancions" l'environnement(recupère les packages requis, dans la version spécifiée dans les 2 fichiers `.toml`):
```julia
(@v1.10) pkg> activate .    # active l'environnement
(@v1.10) pkg> instantiate
```
Un téléchargement et une pré-compilation des packages requis commence, cela peut prendre quelques minutes.

Une fois terminé, vous pouvez utiliser le fichier notebook après avoir démarré Jupyterlab avec un noyau Julia.

