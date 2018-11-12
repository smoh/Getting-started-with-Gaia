# Gaia Archive ADQL query snippets

* 2MASS and allWISE cross-matches

```sql
SELECT
  gaiadr2.gaia_source.designation, gaiadr2.gaia_source.source_id, allwise.*, tmass.*
FROM gaiadr2.gaia_source
-- allwise
LEFT JOIN gaiadr2.allwise_best_neighbour
  on gaiadr2.allwise_best_neighbour.source_id=gaiadr2.gaia_source.source_id
LEFT JOIN gaiadr1.allwise_original_valid as allwise
  on allwise.allwise_oid = gaiadr2.allwise_best_neighbour.allwise_oid
-- tmass
LEFT JOIN gaiadr2.tmass_best_neighbour on
  gaiadr2.tmass_best_neighbour.source_id=gaiadr2.gaia_source.source_id
LEFT JOIN gaiadr1.tmass_original_valid tmass
  on tmass.tmass_oid = gaiadr2.tmass_best_neighbour.tmass_oid
...
```

* PanSTARRS cross-matches

```sql
select
  gaiadr2.gaia_source.designation, gaiadr2.gaia_source.source_id,
  ps.*
from gaiadr2.gaia_source
-- panstarrs
left join gaiadr2.panstarrs1_best_neighbour
  on gaiadr2.panstarrs1_best_neighbour.source_id=gaiadr2.gaia_source.source_id
left join gaiadr2.panstarrs1_original_valid as ps
  on ps.obj_id = gaiadr2.panstarrs1_best_neighbour.original_ext_source_id
...
```

* Get DR1 source_id

```sql
select gaiadr2.gaia_source.source_id, gaiadr2.dr1_neighbourhood.*
from gaiadr2.gaia_source
-- dr1
left join gaiadr2.dr1_neighbourhood
  on gaiadr2.dr1_neighbourhood.dr2_source_id=gaiadr2.gaia_source.source_id
```

* RAVE DR5

```sql
select
  gaiadr2.gaia_source.designation, gaiadr2.gaia_source.source_id, gaiadr2.ravedr5_best_neighbour.*
from gaiadr2.gaia_source
-- ravedr5
left join gaiadr2.ravedr5_best_neighbour
  on gaiadr2.ravedr5_best_neighbour.source_id = gaiadr2.gaia_source.source_id
where ...
```

* Tycho-2

```sql
select gaiadr2.gaia_source.designation, gaiadr2.gaia_source.source_id,
    tyc.hip, tyc.tyc1, tyc.tyc2, tyc.tyc3, tyc.id_tycho, tyc.id
from gaiadr2.gaia_source
-- tycho2
left join gaiadr2.tycho2_best_neighbour on gaiadr2.tycho2_best_neighbour.source_id = gaiadr2.gaia_source.source_id
left join public.tycho2 tyc on gaiadr2.tycho2_best_neighbour.original_ext_source_id = tyc.id
where ...
```
