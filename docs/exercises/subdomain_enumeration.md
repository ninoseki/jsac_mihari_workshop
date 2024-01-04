# CT Based Subdomain Enumeration

Initialize a new rule by:

```bash
mihari rule init ex1.yaml
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

Now you are ready to search by the rule!

```bash
mihari search ex1.yaml
```

!!! tip

    Please do `mihari db migrate` if you get an error like `Could not find table 'rules'`.

Mihari provides two ways to review a search result.

**CLI**

```bash
mihari alert list
```

**Web**

```bash
mihari web
```
