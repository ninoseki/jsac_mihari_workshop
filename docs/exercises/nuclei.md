# Working Along With Nuclei

Try to create a Nuclei template to check the honeypots have an ISO 8601 format datetime in the HTML body.

<figure markdown>
  ![img](https://i.imgur.com/68zeOQn.png)
</figure>

- Nuclei template is explained at https://docs.projectdiscovery.io/templates/introduction

```bash
mihari artifact list "rule.id:{HONEYPOT_RULE_ID}" | jq -r ".results[].data" | nuclei -t /path/to/template
```

!!! note

    Please use the command I give in Slack instead of `mihari alert list ...` if you are unable to complete the previous excercise.
