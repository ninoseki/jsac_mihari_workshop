# Practical Operation With Mihari

<figure markdown>
  ![img](https://lh4.googleusercontent.com/23blMYg73BLMGYmPc4Nnxxjiy_27Q-pugM4Z3QpWuE1klXPNm3o0GCNODJk4nW4Lh7N9wShArD3QthUzPDtuq81EgBnHT6s021nzQn0-LrxeW-qe5zuJk0TXVIr7Eziinl9urOMm6VB5GUyx1gr75CDd7GJcv9j-Usx5bx_YPAPRq8tfzhTOFUxA9AFk8A){: style="height:480px"}
</figure>

---

Using [GitOps](https://www.redhat.com/en/topics/devops/what-is-gitops) methodology is the best practice to use Mihari.

!!! success

    - Easy to review & revert a change in a rule.
    - Easy to build a workflow.

You can use any CI/CD solution (CircleCI, GitHub Actions, etc.) with Mihari.

## GitHub Actions

You need to have the following files:

- [Gemfile](https://github.com/ninoseki/jsac_mihari_workshop/blob/main/Gemfile)
- [Gemfile.lock](https://github.com/ninoseki/jsac_mihari_workshop/blob/main/Gemfile.lock)
- [.github/workflows/mihari.yml](https://github.com/ninoseki/jsac_mihari_workshop/blob/main/.github/workflows/mihari.yml)
- ... and rules!

`Gemfile` and `Gemfile.lock` for caching gem dependencies. `.github/workflows/mihari.yml` is a workflow to run Mihari.
