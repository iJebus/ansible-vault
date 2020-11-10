# Default

Note that for this to work as is currently configured, you'll need to generate certificates and place them in `./tls/`. I like to use [step-ca](https://smallstep.com/docs/step-ca) as follows.

```sh
mkdir tls
cd tls
step certificate create ca ca.crt ca.key --profile root-ca
step certificate create vault server.crt server.key --profile leaf --ca ca.crt --ca-key ca.key --san 172.17.0.4 --san 172.17.0.3 --san 172.17.0.2 --no-password --insecure --not-after 8766h
```

Just comment/delete the relevant part of [prepare.yml](prepare.yml) and modify the vars regarding TLS in [molecule.yml](molecule.yml) if you want out.
