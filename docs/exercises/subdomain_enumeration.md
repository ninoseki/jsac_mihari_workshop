# CT Based Subdomain Enumeration

<figure markdown>
  ![img](https://i.redd.it/28pmaay4f9391.jpg){: style="width:480px"}
</figure>

---

!!! abstract "Learning Points"

    - How to write a rule
    - How to search
    - How to check findings via CLI & build-in web app

Initialize a new rule by:

```bash
mihari rule init ex1.yml
```

Modify `queries`, `enrichers` and `emitters` as the following:

```yaml
queries:
  - analyzer: crtsh
    query: jpcert.or.jp
    exclude_expired: true
    match: ILIKE
emitters:
  - emitter: database
enrichers:
  - enricher: whois
data_types:
  - domain
```

Now you are ready to search.

```bash
mihari search ex1.yml
```

!!! tip

    Please do `mihari db migrate` if you get an error like `Could not find table 'rules'`.

Mihari provides two ways to review a search result.

**CLI**

```bash
mihari alert list
```

**Web app**

```bash
mihari web
```

## How Listing/Searching Works

!!! tip

    Search query supports `AND`, `OR`, `:`, `=`, `!=`, `<`, `<=`, `>`, `>=`, `NOT` and `()`.

Searchable fields are:

| Target     | Searchable fields                                                                                                                                                                                                            |
| ---------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `alert`    | `id`, `tag`, `created_at`, `rule.id`, `rule.title`, `rule.description`, `artifact.data`, `artifact.data_type`, `artifact.source` and `artifact.query`                                                                        |
| `artifact` | `id`, `data`, `data_type`, `source`, `query`, `tag`, `rule.id`, `rule.title`, `rule.description`, `tag`,`created_at`, `asn`, `country_code`, `dns_record.value`, `dns_record.resource`, `reverse_dns_name`, `cpe` and `port` |
| `rule`     | `id`, `title`, `description`, `tag`, `created_at` and `updated_at`                                                                                                                                                           |
| `tag`      | `id` and `name`                                                                                                                                                                                                              |
