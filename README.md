# snapshots
Strategies for data aggregation over time

Say you have a simple app for people to track their exercise. We won't go into great detail, but let's assume you have a central server and when one of your users finishes a jog, that server gets a message that looks something like this

```
{
  "userid": 123,
  "timestamp": 1683498816,
  "distance": 4870,
  "duration": 4560
}
```

indicating that on the afternoon of May 7th, User 123 ran 4870 meters in 4560 seconds. Your ingestion process does a lookup that adds a few useful fields, and what gets dumped into your `events` table is

```
userId | userInstallTimestamp | eventDate | eventTimestamp | distanceMeters | durationSeconds | ingestionTimestamp
-------|----------------------|-----------|----------------|----------------|-----------------|-------------------
123    | 1682888182           | 20230507  | 1683498816     | 4870           | 4560            | 1683498817
```
