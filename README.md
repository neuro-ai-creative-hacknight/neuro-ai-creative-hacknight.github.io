# [neuro-ai-creative-hacknight.github.io](https://neuro-ai-creative-hacknight.github.io)
This is the website of the Neuro AI Creative Hacknight, a satellite event of the OHBM2023 Montréal conference.
The website is built with the [jupyter book](https://jupyterbook.org/) project, and deployed using github.

### Build the book locally
- Clone this repository
- Run `pip install jupyter-book` (recommended in a virtual environment).
- For a fresh build, remove the content of `content/_build/`
- Run `jb build content/`

A static version of the book will be generated on `content/_build/html/`.

### Publishing the book
A [github action](https://github.com/neuro-ai-creative-hacknight/neuro-ai-creative-hacknight.github.io/blob/main/.github/workflows/deploy-book.yml) has been setup to automatically re-build and publish the book every time a change is made to the content of the `main` branch.
- Copy the YAML file into your own .github/workflows/ folder.
- Set the organization workflow permissions to read-write.
- Set the repository's GitHub Pages source to the gh-pages branch. 


### Sources
- Forked from https://github.com/main-educational/main-educational.github.io