# TS_OPENSTACK_RESOURCE_LISTER

These instructions are a work in progress

need to setup node env on your machine
need to install pnpm

`git pull` this repo

create your `.env` file with username and password for the provider

`pnpm install`

Then, to pull resources
`pnpm dev`

to generate s3 private keys
`pnpm dev:creds`

## Tenants Env Variable

encode to base64 then add to .env file an array that looks like this

```js
[
    {
        name: "ruh2",
        base_url: "https://XXXXXX.bluvalt.com",
        tenants: [
            "XXXXXXX",
            "XXXXXXXXXXXXX",
            "XXXXXXXXXXXXXXXX"
        ]
    },
    {
        name: "jed1",
        base_url: "https://XXXXXX.bluvalt.com",
        tenants: [
            "XXXXXXXXX",
            "XXXXXXXXXXXXXXX",
            "XXXXXXXXXXXXXXXXXXXXX"
        ]
    }
]
```
