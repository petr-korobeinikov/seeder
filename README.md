# seeder

The only tool for reproducible seeding volumes and storages (including databases
as well).

## `seeder.yaml` — the :gear: of reproducible seeding

<!-- @formatter:off -->
```yaml
seeder:
  state:
    # seeding postgres data
    - name: postgres file seed
      type: postgres
      config:
        - file: seed.sql

    # seeding s3 data
    - name: s3 plain text file seed
      type: s3
      config:
        - bucket: "bucket"
          object-name: "seeded/file/seed.txt"
          option:
            content-type: text/plain
            content-encoding: utf8
          file: seed.txt

    # seeding vault secrets
    - name: vault file seed
      type: vault
      config:
        - key: "secret/data/seed/file/json"
          file: seed.json
```
<!-- @formatter:on -->

## Docs

- https://petr-korobeinikov.github.io/seeder/

## Quick start

- https://petr-korobeinikov.github.io/seeder/quick-start/

## Tutorials

- `postgres`: https://petr-korobeinikov.github.io/seeder/tutorial/postgres/
- `vault`: https://petr-korobeinikov.github.io/seeder/tutorial/vault/
- `s3`: https://petr-korobeinikov.github.io/seeder/tutorial/s3/
- `kafka`: https://petr-korobeinikov.github.io/seeder/tutorial/kafka/

## Install

- https://petr-korobeinikov.github.io/seeder/install/

## Flags (needs rework 🚧)

- `-c` allows to specify seeder configuration file.
  > Note: dir from config file will be used as working dir for seed files.
- `-seeder-helper $name` shows help for specified seeder.
- `-known` shows known seeders
