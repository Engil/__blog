---
title: Unikernel blog
author: me
---

# Canopy - A git-blogging unikernel

Canopy is an attempt at writting a blog-engine based on Git using [MirageOS][mirage].

The goal is to provide a simple blog platform that requires only a few modifications in a configuration file and a Git repository respecting some architecture rules.

Canopy is written in OCaml using MirageOS and [Irmin][irmin], but it is currently only available on the Unix platform. The Xen platform will be supported as soon as [Decompress][decompress] is ready to be used in Irmin. :-)

## How Canopy works

Canopy will require you to provide a Git remote uri. Once started, it will clone in-memory the repository content and serve the content in a more or less organized way.

Each file at the root of the repository is considered a standalone page, more like the usual « About » or « Contact » pages. They will have their own entries in the navigation menu.

Each directories will contains more pages, but that will be classified under a category decided by the name of the said directory.
For example, a `posts/hello-word.md` file will be a new blog post under the `Posts` category.
You can use it to emulate some sort of tag, like for example having an `OCaml` directory regrouping all you writing in everyone's favorite language. :-)

The file syntax is just plain markdown, everything should be supported out-the-box (depending on the `ocaml-cow` markdown implementation), with a little bit of extra informations absolutely needed at the top of each files.

```
---
title: A blog entry
author: Me
---
article content
```

If you don't respect this syntax, then the article won't show up in the resulting website.

 [decompress]: <https://github.com/oklm-wsh/Decompress>
 [mirage]: <http://mirage.io/>
 [irmin]: <https://github.com/mirage/irmin>
 
 Work in progress
