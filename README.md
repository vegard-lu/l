name: Keep Repository Active

on:
  schedule:
    - cron: '0 0 */89 * *' # Kjør hver 10. dag

jobs:
  update-readme:
    runs-on: ubuntu-latest
    steps:
      - name: Checkout repository
        uses: actions/checkout@v3

      - name: Update README
        run: |
          echo "Automatisk oppdatering $(date)" >> README.md

      - name: Commit and push changes
        run: |
          git config --global user.name "GitHub Actions"
          git config --global user.email "actions@github.com"
          git add README.md
          git commit -m "Automatisk oppdatering for å holde repositoryet aktivt"
          git push# G
