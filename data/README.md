# Learning capture data

This directory defines the JSON layout used by Learning Mode accounts and exports.

The app is a static browser page, so it cannot silently write camera data into this checked-out directory. Live sessions are stored privately in IndexedDB for the current browser origin. The JSON button exports a portable file whose `storage.logicalPath` matches this layout:

```text
data/
  guest/sessions/<session-id>.json
  users/<local-profile-id>/sessions/<session-id>.json
  schemas/account.schema.json
  schemas/learning-session.schema.json
```

Guest is created automatically and requires no login. Named accounts are device-local profiles, not authenticated or cloud-synced users. `file://`, localhost, and a deployed website are different browser origins and therefore keep separate account/session databases.

Exported session JSON can be copied into its logical path when a checked-in fixture is intentionally needed. Real camera captures are ignored by Git by default because face and gesture landmarks may be sensitive.
