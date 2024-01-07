# Vs. ProjectDiscovery or How I Learned to Stop Worrying and Love It

<figure markdown>
  ![img](https://i.imgur.com/RrlRtT7.jpg){: style="width:480px"}
</figure>

---

## A Key Difference

- Mihari is a **passive** monitoring tool
- ProjectDiscovery's Nuclei is an **active** monitoring tool

Nuclei can validate/filter search results by scanning and Mihari cannot.

## Misc Differences

- A number of services supports
  - Mihari supports **15+** services
  - Nuclei (Uncover) supports **10** services
- Data persistence
  - Mihari **does support** data persistence (in SQL database)
  - Nuclei **does support** data persistence (in Elasticsearch, Splunk and ProjectDiscovery's Cloud Platform) by using the reporting feature
    - But it doesn't check the uniqueness of a finding like Mihari does (low confidence)
- Data enrichment
  - Mihari **does have** automated data enrichment feature
  - Nuclei **doesn't have** automated data enrichment feature

## So, So What?

<figure markdown>
  ![img](https://i0.wp.com/jtmat.co.uk/wp-content/uploads/2021/05/Picture1.jpg?resize=293%2C226&ssl=1)
</figure>

I don't know. :D

It depends on what you are trying to do. ProjectDiscovery may be more the right toolset for you.

## A Good Pairing?

<figure markdown>
  ![img](https://i.redd.it/zu1ed7d9cs521.jpg){: style="width:480px"}
</figure>

Anyway you can combine both. Collecting data in Mihari and validating it with Nuclei.

For example:

```bash
mihari artifact list "rule.id:{RULE_ID}" | jq -r ".results[].data"
```
