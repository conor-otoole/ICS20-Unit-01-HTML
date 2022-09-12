#################################################

# Run Mr Coxall's Super Linter against code base #

##################################################



---

name: Mr Coxall's Super Linter



on: [push, pull_request]



jobs:

  run-linters:

    name: Mr Coxall's Super Linter

    runs-on: ubuntu-latest



    steps:

      - name: Check out Git repository

        uses: actions/checkout@main



      # remove section if you do not have any htm, js or ts files!

      - name: Prettify code

        uses: Mr-Coxall/prettier_action@main

        with:

          # run Prettier and change code that needs fixing, before next section

          prettier_options: --write **/*.{html,css,js,ts,jsx,tsx,json}

          GITHUB_TOKEN: ${{ secrets.GITHUB_TOKEN }}



      - name: Run GitHub Super Linter

        uses: github/super-linter@main

        env:

          VALIDATE_ALL_CODEBASE: true

          LINTER_RULES_PATH: /

          VALIDATE_CLANG_FORMAT: false

          VALIDATE_JAVASCRIPT_STANDARD: false

          VALIDATE_PYTHON_FLAKE8: false

          VALIDATE_GITLEAKS: false # for secrets detection

          VALIDATE_JSCPD: false # for copy and paste detection

          DEFAULT_BRANCH: main

          GITHUB_TOKEN: ${{ secrets.GITHUB_TOKEN }}

Then place the following code in a README.md file in your root folder

Make sure you replace <OWNER> with your Github Account name, and <REPOSITORY> with the name of your project!

[![Mr Coxall's Super Linter](https://github.com/<OWNER>/<REPOSITORY>/workflows/Mr%20Coxall's%20Super%20Linter/badge.svg)](https://github.com/<OWNER>/<REPOSITORY>/actions/)


If you want this opened in Repl.it:

[![Run on Repl.it](https://repl.it/badge/github/<OWNER>/<REPOSITORY>)](https://repl.it/github/<OWNER>/<REPOSITORY>)


If the root of the repo is your website then:

This site can be found at: [https://<OWNER>.github.io/<REPOSITORY>](https://<OWNER>.github.io/<REPOSITORY>)
