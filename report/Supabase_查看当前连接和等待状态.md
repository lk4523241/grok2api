| pid     | usename        | application_name                | state               | wait_event_type | wait_event | running_for             | query                                                                                                                                                                                                                                                                                                        |
| ------- | -------------- | ------------------------------- | ------------------- | --------------- | ---------- | ----------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| 4144    | authenticator  | PostgREST 14.5                  | idle                | Client          | ClientRead | 10 days 14:58:00.363398 | LISTEN "pgrst"                                                                                                                                                                                                                                                                                               |
| 974042  | supabase_admin |                                 | idle                | Client          | ClientRead | 13:49:49.30095          | show archive_mode;                                                                                                                                                                                                                                                                                           |
| 813987  | pgbouncer      | Supavisor (auth_query)          | idle                | Client          | ClientRead | 00:00:10.520689         | SELECT * FROM pgbouncer.get_auth($1)                                                                                                                                                                                                                                                                         |
| 4578    | supabase_admin | postgres_exporter               | idle                | Client          | ClientRead | 00:00:07.068154         | with normalized_pg_stat_statements as (
    select
        calls,
        -- Truncate query by 10000 characters, because likely we don't need more than that in WHERE clauses
        lower(regexp_replace(trim(left(query, 10000)), E'\\s+', ' ', 'g')) as query
    from
        extensions.pg_stat_statem |
| 1036313 | postgres       | Supavisor                       | idle in transaction | Client          | ClientRead | 00:00:00.181711         | SELECT "id" FROM "client_keys" WHERE "client_keys"."id" = $1 ORDER BY "client_keys"."id" LIMIT $2 FOR UPDATE                                                                                                                                                                                                 |
| 1036317 | postgres       | supabase/dashboard-query-editor | active              | null            | null       | 00:00:00                | select
  pid,
  usename,
  application_name,
  state,
  wait_event_type,
  wait_event,
  now() - query_start as running_for,
  left(query, 300) as query
from pg_stat_activity
where datname = current_database()
order by query_start nulls last limit 100;

-- source: dashboard
-- user: sessi |
| 4136    | supabase_admin | pg_net 0.20.3                   | idle                | Extension       | Extension  | null                    |                                                                                                                                                                                                                                                                                                              |
| 4137    | supabase_admin | pg_cron scheduler               | null                | Extension       | Extension  | null                    |                                                                                                                                                                                                                                                                                                              |