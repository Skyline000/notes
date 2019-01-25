# MySQL event task

 MySQL event task

```sql
SET GLOBAL event_scheduler = ON;

CREATE EVENT IF NOT EXISTS event_clean_trigger_memberinfo
ON SCHEDULE EVERY 1 DAY STARTS '2019-01-21 05:00:00' ON COMPLETION PRESERVE ENABLE 
DO
  DELETE FROM membership.trigger_memberinfo WHERE creation_date < NOW() - INTERVAL 90 DAY;
```

