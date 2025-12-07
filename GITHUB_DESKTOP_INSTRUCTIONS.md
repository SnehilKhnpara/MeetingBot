# GitHub Desktop Instructions

## Quick Setup (Easiest Method)

### Step 1: Copy These Files to Your Local Repository

Copy these **4 NEW files** to your local `meetingBot1` repository:

1. **`AUDIO_CHUNK_FIXES.md`** - Documentation (474 lines)
2. **`src/audio_chunk_manager.py`** - New audio capture loop (380 lines)
3. **`test_audio_chunks.py`** - Integration test (226 lines)
4. **`view_chunks.py`** - Chunk viewer utility (223 lines)

### Step 2: Update These **2 EXISTING files**:

1. **`src/models.py`** - Replace with updated version
2. **`src/session_manager.py`** - Replace with updated version

---

## Method 1: Apply Patch File (Recommended)

### Using Git Bash or Terminal:

```bash
# Navigate to your local repository
cd path/to/meetingBot1

# Apply the patch
git apply audio-capture-fix.patch

# Check what changed
git status

# Commit in GitHub Desktop
```

---

## Method 2: Manual Copy (If patch doesn't work)

### Files Location in This Environment:

**New Files (copy these):**
- `/home/user/MeetingBot/AUDIO_CHUNK_FIXES.md`
- `/home/user/MeetingBot/src/audio_chunk_manager.py`
- `/home/user/MeetingBot/test_audio_chunks.py`
- `/home/user/MeetingBot/view_chunks.py`

**Modified Files (replace these):**
- `/home/user/MeetingBot/src/models.py`
- `/home/user/MeetingBot/src/session_manager.py`

### Steps:

1. Copy all 6 files from this environment to your local `meetingBot1` folder
2. Open **GitHub Desktop**
3. You'll see 6 changed files in the left panel
4. Review the changes (green = added, yellow = modified)
5. Create a new branch: `claude/fix-participant-tracking-01Cyn9fMN3PuruEjoHEFFUtG`
6. Add a commit message (see below)
7. Click "Commit to claude/fix-participant-tracking-01Cyn9fMN3PuruEjoHEFFUtG"
8. Click "Push origin"

---

## Commit Message for GitHub Desktop

**Summary:**
```
Fix audio capture and participant tracking pipeline
```

**Description:**
```
CRITICAL FIXES:

1. Audio Loop Integration (session_manager.py)
   - Fixed broken audio_capture_loop calling non-existent capture_chunk()
   - Now correctly calls audio_loop.run() method
   - Properly updates session.audio_chunks counter

2. Unified Chunk Data Model (models.py)
   - Added AudioChunkData model with complete chunk information
   - Added ParticipantSnapshot for participant tracking per chunk
   - Added SpeakerInfo for active speaker detection
   - Includes automatic filename generation with participants/speaker

3. Improved Audio Capture Loop (audio_chunk_manager.py)
   - Fixed duplicate chunk counter increments (was incrementing twice)
   - Fixed unreachable speaker diarization code
   - Proper 30-second chunking with no gaps
   - Participant snapshots captured per chunk
   - Speaker detection integrated correctly
   - Predictable file naming: chunk_001_bot_user1_2025-02-15T10-20-00.wav
   - Saves chunk metadata as JSON

4. Session Manager Integration (session_manager.py)
   - Passes participant info to audio loop every 30 seconds
   - Uses ImprovedAudioCaptureLoop instead of broken implementation
   - Maintains concurrent loops (participants, audio, captions)

TESTING & UTILITIES:
- test_audio_chunks.py: Integration test for chunk capture
- view_chunks.py: Utility to view and verify chunk data
- AUDIO_CHUNK_FIXES.md: Comprehensive documentation

ROOT CAUSES RESOLVED:
✅ Audio files now created (previously failed completely)
✅ Chunks numbered consistently (0,1,2 not 0,2,4)
✅ Speaker detection runs on valid audio (not unreachable code)
✅ Unified data model (not scattered events)
✅ Proper file naming with context
✅ Participant tracking per chunk
✅ Production-ready, scalable, concurrent

See AUDIO_CHUNK_FIXES.md for detailed analysis and migration notes.
```

---

## Create Pull Request

After pushing, go to:
https://github.com/SnehilKhnpara/meetingBot1/pulls

1. Click "New pull request"
2. Select your branch: `claude/fix-participant-tracking-01Cyn9fMN3PuruEjoHEFFUtG`
3. Add title: "Fix audio capture and participant tracking pipeline"
4. Add description (use commit message above)
5. Create pull request

---

## Files Summary

```
✅ 4 New Files Created:
   - AUDIO_CHUNK_FIXES.md (documentation)
   - src/audio_chunk_manager.py (improved audio loop)
   - test_audio_chunks.py (integration test)
   - view_chunks.py (chunk viewer)

✅ 2 Files Modified:
   - src/models.py (added AudioChunkData model)
   - src/session_manager.py (fixed audio loop integration)

📊 Total: 1,429 lines added, 13 lines removed
```
