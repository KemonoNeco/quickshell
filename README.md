# e621 Integration for Quickshell

This repository contains modifications to add e621.net support to the Quickshell booru service.

## ⚠️ Disclaimer

**This README and project is unreviewed AI-generated slop and *will* contain inaccuracies or errors.**

## Changes

### e621 Provider Support

Added e621.net as a booru provider in `ii/services/Booru.qml`:

- **API Endpoint**: `https://e621.net/posts.json`
- **Tag Search**: `https://e621.net/tags.json`
- **Description**: "Furry art | Great quantity, lots of NSFW, quality varies"

### Implementation Details

The e621 integration includes:

1. **Response Mapping**: Handles e621's API response format which can return either:
   - An object with a `posts` array
   - An array directly

2. **Tag Processing**: e621 organizes tags by category (general, artist, character, copyright, species, etc.). The implementation flattens all category tags into a single space-separated string.

3. **File URL Handling**: Extracts file URLs from the nested `file`, `preview`, and `sample` objects in the e621 response structure.

4. **User-Agent Header**: Sets a User-Agent header for API requests (required by e621, similar to Danbooru).

5. **Tag Search**: Implements tag autocomplete using e621's tag search API with the `name_matches` parameter.

### Files Modified

- `ii/services/Booru.qml` - Added e621 provider configuration (lines 275-337) and User-Agent handling (lines 519-522, 571-574)

