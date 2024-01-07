# Practical Operation With Mihari

<figure markdown>
  ![img](https://lh4.googleusercontent.com/23blMYg73BLMGYmPc4Nnxxjiy_27Q-pugM4Z3QpWuE1klXPNm3o0GCNODJk4nW4Lh7N9wShArD3QthUzPDtuq81EgBnHT6s021nzQn0-LrxeW-qe5zuJk0TXVIr7Eziinl9urOMm6VB5GUyx1gr75CDd7GJcv9j-Usx5bx_YPAPRq8tfzhTOFUxA9AFk8A){: style="width:480px"}
</figure>

Using [GitOps](https://www.redhat.com/en/topics/devops/what-is-gitops) methodology is the best practice to use Mihari.

!!! success

    - Easy to review & revert a change in a rule
    - Easy to build a workflow

You can use any CI/CD solution (CircleCI, GitHub Actions, etc.) with Mihari.

For example, the following is a GitHub Actions workflow to run Mihari with assuming you have a PostgreSQL.

```yaml
name: Mihari searches

on:
  schedule:
    - cron: "0 1 * * *"
  workflow_dispatch:

jobs:
  search:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
      - name: Install dependencies
        run: sudo apt-get -yqq install libpq-dev
      - name: Set up Ruby 3.3
        uses: ruby/setup-ruby@v1
        with:
          ruby-version: "3.3"
          bundler-cache: true
      - name: Search
        env:
          DATABASE_URL: ${{ secrets.DATABASE_URL }}
        run: bundle exec mihari search -f /path/to/rule.yml
```
