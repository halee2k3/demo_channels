# Mobile App QA Playlist Fixtures

These M3U files are generated from the supplied `demo_playlist.m3u`.

## Files
- `baseline.m3u`: Original playlist snapshot.
- `changed.m3u`: Removes one channel, renames one channel, changes one stream URL, and adds one synthetic QA channel.
- `no-change.m3u`: Identical content to `baseline.m3u`.
- `big-drop-20.m3u`: Contains 20 fewer channel entries than `baseline.m3u`.

## Important usage notes
1. Import `baseline.m3u` first and let the app create its initial snapshot.
2. To test a change against the *same source URL*, host `baseline.m3u` at a URL, then replace its contents with `changed.m3u` (or `no-change.m3u`) while keeping the URL/path unchanged. Do not simply edit the playlist URL in the app if the app treats that as a new playlist.
3. For Big Drop, first snapshot `baseline.m3u`, then replace the content at the same hosted URL with `big-drop-20.m3u`.
4. `changed.m3u` includes a synthetic `example.com` stream URL. It is intended to test playlist parsing/change detection, not video playback.
5. The Big Drop fixture removes 20 entries from the baseline. Whether this triggers the app's Big Drop notification depends on the app's exact threshold logic (e.g. 20 or more vs. greater than 20) and its channel identity matching rules.
6. Public Git hosting/CDN caching may delay updated content. Verify the Raw URL returns the new content before pressing "Check for changes now".
