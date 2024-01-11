# Working Along With Nuclei

<figure markdown>
  ![img](https://preview.redd.it/abx0po3jd2b21.jpg?auto=webp&s=76ded31ff8fdaa7caad349b3559749e3fbfc1830){: style="width:480px"}
</figure>

---

!!! abstract "Learning Points"

    - How to use `list-transform` feature.
    - How to use Nuclei along with Mihari.

## Problem Statement

Try to create a Nuclei template that meets all of the following conditions:

- HTTP status equals to 200.
- Headers have `x-conference:JSAC2024`.
- HTML body has an ISO 8601 format datetime.

<figure markdown>
  ![img](https://i.imgur.com/68zeOQn.png)
</figure>

## Notes

### `list-transform` Basics

`list-transform` command is for listing/searching data with transformation. More specifically, you can transform data with [Jbuilder](https://github.com/rails/jbuilder).

For example, the following command outputs artifacts data as a top-level array.

```bash
mihari artifact list-transform -t "json.array! results.map(&:data)"
```

More practically, the following Jbuilder template combines an IP and its associated ports.

**ip_port.json.jbuilder**

```ruby
ip_ports = results.map do |artifact|
  artifact.ports.map do |port|
    "#{artifact.data}:#{port.port}"
  end
end.flatten

json.array! ip_ports
```

```bash
mihari artifact list-transform -t /path/to/ip_port.json.jbuilder
```

The output can be used for passing data into Nuclei.

!!! warning

    With great power comes great responsibility.

    Jbuilder can execute anything with the same privilege Mihari has. Do not use untrusted template.

### Nuclei Basics

- Nuclei template is explained at https://docs.projectdiscovery.io/templates/introduction

**Example**

For example, let's scan the Hello World Rack application.

```bash
# Start Rack application
rackup config.ru
```

```bash
# Open another terminal
echo "localhost:9292" | nuclei -t nuclei/hello_world.yaml
```

### `list-transform` + Nuclei

The following command passes `ip:port` formatted data (targets) to Nuclei.

```bash
# Confirm before scanning
$ mihari artifact list-transform "rule.id:{HONEYPOT_RULE_ID}" -t ip_port.json.jbuilder | jq -r ".[]"
# Scan if the output looks good
$ mihari artifact list-transform "rule.id:{HONEYPOT_RULE_ID}" -t ip_port.json.jbuilder | | jq -r ".[]" |  nuclei -t /path/to/template
```

!!! note

    Please follow an instruction I give in Slack instead of `mihari artifact list-transform ...` if you are unable to complete the previous exercise.
