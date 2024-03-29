# Finding Honeypots

<figure markdown>
  ![img](https://i.kym-cdn.com/photos/images/newsfeed/000/993/358/f68.png){: style="width:480px"}
</figure>

---

!!! abstract "Learning Points"

    - How to write a rule. (Reprise)

## Problem Statement

I run two [HASH](https://github.com/DataDog/HASH) based honeypots on the Internet.

!!! warning

    I will tear down the honeypots after the conference. I don't assure their existence after 2024/01/26.

Try to create a Mihari rule to find them.

## Notes

- HASH's profile configuration is described at https://github.com/DataDog/HASH/blob/main/docs/config.md.
- The honeypot profile is defined in https://github.com/ninoseki/jsac_mihari_workshop/tree/main/honeypot.
- Alternatively you can run the honeypot in your laptop by:

```bash
# Node.js v20+ is required
git clone https://github.com/ninoseki/jsac_mihari_workshop
cd jsac_mihari_workshop
npm install
npx hash-honeypot run honeypot
```

!!! tip

    - There is a very unique header key-value pair.
    - Favicon is very unique too.
