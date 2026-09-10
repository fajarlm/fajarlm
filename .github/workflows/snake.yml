name: Generate Snake

on:
  schedule:
    - cron: "0 */6 * * *"   # jalan tiap 6 jam
  workflow_dispatch: {}
  push:
    branches:
      - main

jobs:
  generate:
    permissions:
      contents: write
    runs-on: ubuntu-latest
    steps:
      - name: Generate contribution snake SVG/GIF
        uses: Platane/snk@v3
        with:
          github_user_name: fajarlm
          outputs: |
            dist/github-contribution-grid-snake.svg
            dist/github-contribution-grid-snake-dark.svg?palette=github-dark
            dist/github-contribution-grid-snake.gif?color_snake=orange&color_dots=#bfd6f6,#8dbdff,#64a1f4,#4489e8,#2b6cd4

      - name: Push output to output branch
        uses: crazy-max/ghaction-github-pages@v4
        with:
          target_branch: output
          build_dir: dist
        env:
          GITHUB_TOKEN: ${{ secrets.GITHUB_TOKEN }}
