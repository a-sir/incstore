# incstore
Key-attributes storage with history of changes.

## Use cases.
        1. Give me last versions of key-value pairs;
        2. Give me last versions of key-value for keys, suitable for some condition;
        3. Give me all modifications for key=key1 in last N days;
        4. Give me all changes for group of keys in last N days;

## Example.

        We keep key-attributes storage on disk and space-separated files.
        key1 attr1 attr2
        key2 attr2 attr2

        Useful to grep values, but not possible to see history of changes.

## Requirements.
        Key + values are <1kb, key < 200b
        Data splitted by keys to buckets. Keys allow to group frequently used together data in single bucket;

        Since most frequent operation is working with last state, last versions access speed should have a #1 priority;
        History of changes for a group of keys (last < 5 changes) for 1m of keys should be available in minutes, degraging lineary of count of keys;
