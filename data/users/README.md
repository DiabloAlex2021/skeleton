# Local-profile exports

Named accounts require no login and exist only in the current browser. Their learning sessions use `data/users/<local-profile-id>/sessions/<session-id>.json` as the portable export layout.

Removing a local profile in the app preserves its recordings by moving their storage ownership to Guest while retaining the original capture-time owner snapshot.
