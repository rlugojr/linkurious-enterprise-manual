# Audit trail

## Configuration

Linkurious enterprise is shipped with an Audit Trail feature. This feature allows you to have detailed logs about the operations performed on your graph database by Linkurious.
To configure the audit trail system, edit the file `linkurious/data/config/production.json`. Add the following to the exported object:

```json
"auditTrail": {
  "enabled": true,
  "logFolder": "audit-trail",
  "fileSizeLimit": 5242880,
  "logResult": false,
  "strictMode": false,
  "mode": "rw"
}
```

- `enabled`: must be true to enable this feature
- `logFolder`: where to store the log file. This path is relative to the `data` directory located at the root of your Linkurious installation
- `fileSizeLimit`: maximum size in byte of a log file. The audit-trail system performs files rotations in order to avoid enormous log files
- `logResult`: set it to `true` to log the result of the performed operation and not only the operation itself
- `strictMode`: set it to `true` to ensure that the operation has been logged before returning the result to the user. Might have a big impact on the server responsiveness
- `mode`: `rw` to log read and write actions. `r` to log only read actions. `w` to log only write actions.


## Log format
The logs are JSON lines. You can easily bind a log management system like Log Stash to interpret them.