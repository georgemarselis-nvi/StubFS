# StubFS

A stub filesystem to handle POSIX access to offline files with recall trigger logic. 

StubFS is a FUSE-based user-space filesystem that transparently exposes cold-storage files as lightweight placeholders (stubs) in the live filesystem. When a stub is accessed—read, mmap’d, or opened—StubFS intercepts the call, triggers a recall request via Aurora and Tundra, and blocks the operation until the file is available locally. It enables seamless integration of offline data stored in tape-backed tiers managed by Spool, without breaking POSIX expectations.

StubFS also supports extended attributes for recall status, integrates with per-user policies, and logs recall attempts for quota/audit tracking. It is the critical glue enabling BeeGFS tiering to expose deep storage in a usable, transparent form.
