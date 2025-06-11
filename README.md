# PostgreSQL-Migration
1. Prevent Connections to Old Server: Change the PostgreSQL port or use firewall rules to block new connections.
2. Set Up New Server: Create all users, roles, and databases on the new server.
3. Backup Old Server Data:
```
  Take a full database dump using pg_dump or pg_dumpall.
  Generate a structured backup for GRANT and ALTERED privileges separately.
```
4. Verify Object Count Before Migration:
```
Fetch all object counts (tables, indexes, sequences, functions) from the old server.

Use queries like SELECT count(*) FROM pg_tables; or similar for other objects.
```
5. Restore Data on New Server:
```
Restore the full dump using pg_restore.

Apply the GRANT and ALTERED privileges backup to maintain user permissions.
```
6. Verify Data Integrity:
```
Compare object counts before and after migration.
Run consistency checks using pg_stat_all_tables and pg_stat_all_indexes.
```
7. Test User Access & Functionality:
```
Ensure users can connect without issues.
Validate queries, functions, and performance.
```

Additional Considerations:
```
 -Index Rebuilds: Ensure indexes are properly restored and optimized.

-Vacuum & Analyze: Run VACUUM ANALYZE for performance optimization.

-Replication & Failover Setup: If using replication, configure streaming replication on the new server.

-Backup New Server: After a successful migration, take a fresh backup from the new server.
```
