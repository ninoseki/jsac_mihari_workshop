# Architecture

<figure markdown>
  ![img](https://upload.wikimedia.org/wikipedia/commons/thumb/9/9f/Montreal_-_QC_-_Habitat67.jpg/750px-Montreal_-_QC_-_Habitat67.jpg){: style="width:480px"}
</figure>

---

Mihari is a packaged as a Ruby gem and uses the following components:

- [rails/thor](https://github.com/rails/thor) for building the CLI application.
- [ruby-grape/grape](https://github.com/ruby-grape/grape), [rack/rack](https://github.com/rack/rack) and [puma/puma](https://github.com/puma/puma) for building and running the web application.
- [sidekiq/sidekiq](https://github.com/sidekiq/sidekiq) for (optional) background processing.
- [vuejs](https://github.com/vuejs/) for building the frontend SPA.

## Basic

```mermaid
flowchart LR
    CLI["CLI\n(Thor)"] --> Database
    Web["Web\n(Grape on Rack + Puma)"] --> Database
```

The lab env uses this one.

## Advanced

```mermaid
flowchart LR
    CLI["CLI\n(Thor)"] --> Database
    Web["Web\n(Grape on Rack + Puma)"] --> Database
    Web --> Sidekiq["Job Queue\n(Sidekiq)"]
    Sidekiq --> Database
    Sidekiq --> Redis
```

This one is recommended if you want to use the API a lot.

Sidekiq handles time-consuming jobs such as searching a rule, etc.

!!! note

    The web application runs on Rack + Puma. Its default HTTP request timeout is 60s. It means that a search exceeds 60s will fail.
