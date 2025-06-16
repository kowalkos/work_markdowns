---
id: tworzeniearchiwalneparagony
aliases:
  - tworzenieArchiwalneParagony
tags: []
---

# tworzenieArchiwalneParagony

Wiadomości

- mamy zewnętrzne cassandy (cassandra_Asia) do niej wpadają paragony z marketu 3

1. wchodzimy na środowisko gdzie mamy postawioną cassandre
2. wchodzimy do bazy
3. tworzymy osobną tabelke dla tylko archiwalnych paragonów (używamy skryptu)

CREATE TABLE m4c_dev_test.receipt (
ou text,
de text,
cr int,
tn int,
rgz blob,
PRIMARY KEY ((ou, de, cr), tn)
) WITH CLUSTERING ORDER BY (tn ASC)
AND read_repair_chance = 0.0
AND dclocal_read_repair_chance = 0.1
AND gc_grace_seconds = 0
AND bloom_filter_fp_chance = 0.01
AND caching = { 'keys' : 'ALL', 'rows_per_partition' : 'NONE' }
AND comment = ''
AND compaction = { 'class' : 'org.apache.cassandra.db.compaction.SizeTieredCompactionStrategy', 'max_threshold' : 32, 'min_threshold' : 4 }
AND compression = { 'enabled' : 'false' }
AND default_time_to_live = 0
AND speculative_retry = '99PERCENTILE'
AND min_index_interval = 128
AND max_index_interval = 2048
AND crc_check_chance = 1.0
AND memtable_flush_period_in_ms = 0;

4. aby odpalić na lokalnym środowisku sobie można dodać
![[Pasted image 20240918132727.png]]![[Pasted image 20240919150307.png]]