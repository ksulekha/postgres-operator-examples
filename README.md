# [PGO](https://github.com/CrunchyData/postgres-operator), Crunchy [Postgres Operator](https://github.com/CrunchyData/postgres-operator) Examples

This repository contains examples for deploying PGO, the Postgres Operator from Crunchy Data, using a variety of examples.

The examples are grouped by various tools that can be used to deploy them.

The best way to get started is to fork this repository and experiment with the examples.

Each of the examples has its own README that guides you through the process of deploying it.

You can find the full [PGO documentation](https://access.crunchydata.com/documentation/postgres-operator/v5/) for the project here:

[https://access.crunchydata.com/documentation/postgres-operator/v5/](https://access.crunchydata.com/documentation/postgres-operator/v5/)

You can find out more information about [PGO](https://github.com/CrunchyData/postgres-operator), the [Postgres Operator](https://github.com/CrunchyData/postgres-operator) from [Crunchy Data](https://www.crunchydata.com) at the project page:

[https://github.com/CrunchyData/postgres-operator](https://github.com/CrunchyData/postgres-operator)


```hcl
kind: PostgresCluster
metadata:
  name: hippo
spec:
  image: registry.developers.crunchydata.com/crunchydata/crunchy-postgres:ubi8-14.2-1
  postgresVersion: 14
  instances:
    - name: instance1
      dataVolumeClaimSpec:
        accessModes:
        - "ReadWriteOnce"
        storageClassName: nfs-client
        resources:
          requests:
            storage: 1Gi
  backups:
    pgbackrest:
      image: registry.developers.crunchydata.com/crunchydata/crunchy-pgbackrest:ubi8-2.38-0
      repos:
      - name: repo1
        volume:
          volumeClaimSpec:
            accessModes:
            - "ReadWriteOnce"
            storageClassName: nfs-client
            resources:
              requests:
                storage: 1Gi
                
                
                
                
kubectl exec -n postgres-operator -it hippo-instance1-4zkj-0 /bin/bash

psql postgresql://hippo:%3A7o;IoNY;%286Vg7cB=%40z%40sZJ%3E@hippo-primary.default.svc:5432/hippo


create user user_name with encrypted password 'mypassword';

CREATE DATABASE testdb

\c testdb

CREATE TABLE phonebook(phone VARCHAR(32), firstname VARCHAR(32), lastname VARCHAR(32), address VARCHAR(64));

INSERT INTO phonebook(phone, firstname, lastname, address) VALUES('+1 123 456 7890', 'John', 'Doe', 'North America');

SELECT * FROM phonebook ORDER BY lastname;
```
