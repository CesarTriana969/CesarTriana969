name: Generate snake animation

on:
  schedule:
    - cron: "0 */12 * * *"   # se regenera cada 12 horas
  workflow_dispatch:          # botón para ejecutarlo a mano
  push:
    branches:
      - main

permissions:
  contents: write

jobs:
  generate:
    runs-on: ubuntu-latest
    timeout-minutes: 10
    steps:
      - name: Generate snake SVGs
        uses: Platane/snk@v3
        with:
          github_user_name: ${{ github.repository_owner }}
          outputs: |
            dist/github-snake.svg?color_snake=#6D5DFC&color_dots=#EBEDF0,#C6E9F2,#8FD9EA,#4FC3DC,#14A3B8
            dist/github-snake-dark.svg?palette=github-dark&color_snake=#F38020&color_dots=#161B22,#1E2A4A,#3B3F9E,#6D5DFC,#14F1D9

      - name: Push to output branch
        uses: crazy-max/ghaction-github-pages@v4
        with:
          target_branch: output
          build_dir: dist
        env:
          GITHUB_TOKEN: ${{ secrets.GITHUB_TOKEN }}
