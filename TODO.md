- Cumulative playlist improvements
    - Make date first scraped more prominent, add it to pretty playlists
    - Clean up near-duplicates in cumulative playlists
        - Key: title, artists, and duration
            - Check that this doesn't have false positives
        - Album can (and often does) differ:
            - https://open.spotify.com/track/2nG54Y4a3sH9YpfxMolOyi
            - https://open.spotify.com/track/2z0IupRlVRlDN5r2IVqHyN
    - Update data for all tracks, not just current tracks
        - How to handle tracks that are removed from Spotify

- Features
    - Sort playlists with >9 duplicate names in correct order
    - Automatically add alias for empty playlist names (best effort)
    - Debug perf issues: https://github.com/github/git-sizer
        - Add intermediate directories to playlist dirs
        - The `.git` directory is too big. Perhaps I can delete blobs for old
          cumulative data, since the history is part of the file itself? Must
          retain commit history for plain/ and pretty/ directories, though.
    - https://next.github.com/projects/flat-data
    - Automatically generate aliases for personalized playlists

- Codebase
    - More unit tests for playlist updater
        - only_fetch_these_playlists
    - Fix code complexity of playlist updater
    - Merge cumulative regeneration code
    - Create separate classes for Spotify API and playlist data
        - Spotify has no concept of "original" vs "unique" name
        - Use Pydantic for serde for both sets of classes
    - Measure code coverage and add missing tests
        - .coveragerc file should include:
          [report]
          exclude_lines = @external
    - Play around with Spotipy: https://github.com/spotipy-dev/spotipy
