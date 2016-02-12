# Audit trail

## Configuration

Linkurious Enterprise is shipped with an Audit Trail feature. This feature allows you to record detailed logs about the operations performed on your graph database by users of Linkurious Enterprise.
To configure the audit trail system, edit the file `linkurious/data/config/production.json`. Add the following to the object:

```json
"auditTrail": {
  "enabled": true,
  "logFolder": "audit-trail",
  "fileSizeLimit": 5242880,
  "strictMode": false,
  "mode": "rw"
}
```

* **enabled** - `false`. Enable the audit trail recording if `true`.
* **logFolder** - `"audit-trail"`. Where to store the log files. This path is relative to the `data` directory located at the root of your Linkurious installation.
* **fileSizeLimit** - `5242880`. Maximum size in byte of one log file (default: 5MB). A new file is created when the limit is reached (files rotations) to avoid enormous log files.
* **strictMode** - `false`. Ensure that the operation has been logged before returning the result to the user if `true`. Might have a big impact on the server responsiveness.
* **mode** - `"rw"`. Will record READ actions (`"r"`), WRITE actions (`"w"`), or both (`"rw"`).


## Log format
The logs are JSON lines. You can easily bind a log management system like Log Stash to interpret them. Sample:

```json
{"mode":"READ","date":"2015-10-11T11:05:21.888Z","user":"seb@linkurio.us","sourceKey":"2c08a4d9","action":"getEdge","params":{"edgeId":23}}
{"mode":"READ","date":"2015-10-11T11:05:21.889Z","user":"jean@linkurio.us","sourceKey":"2c08a4d9","action":"getNode","params":{"id":157}}
{"mode":"READ","date":"2015-10-11T11:05:21.910Z","user":"seb@linkurio.us","sourceKey":"2c08a4d9","action":"getNode","params":{"id":832}}
```