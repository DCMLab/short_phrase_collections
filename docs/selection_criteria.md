# Stimulus Selection Criteria

This document describes the criteria used to select musical phrases for the iterative music reduction experiment.

## Overview

The stimuli are designed for a behavioral paradigm where participants iteratively remove notes from polyphonic excerpts, selecting at each step the note whose removal alters the music least. This requires carefully selected phrases that are:

1. Short enough for participants to maintain a mental representation
2. Structurally coherent and tonally closed
3. Rich enough in polyphonic texture to support hierarchical reduction

## Inclusion Criteria

### Length
- **Target**: 8 bars (range: 8-16 bars)
- **Rationale**: Short enough for working memory, long enough for structural complexity

### Tonal Coherence
- Must begin and end in the same key, OR
- Must modulate away and return to the original key
- **Rationale**: Provides clear structural boundaries for the reduction task

### Polyphonic Texture
- Must contain multiple voices (typically 2-4)
- Must have both horizontal (melodic) and vertical (harmonic) organization
- Variable number of active voices across measures is acceptable
- **Rationale**: Tests participants' ability to perceive and prioritize different structural dimensions

### Structural Completeness
- Must constitute a complete phrase or period
- Should have clear beginning and ending gestures
- **Rationale**: Ensures the excerpt has internal structural logic

### Historical Period
- Baroque to Classical period (approx. 1680-1800)
- **Rationale**: Common-practice tonality with established harmonic conventions

## Exclusion Criteria

- Excerpts with extreme tempo markings
- Pieces requiring extensive ornament realization
- Fragments without clear phrase boundaries
- Excerpts with ambiguous or experimental tonality

## Preprocessing

### Deduplication
Some excerpts (particularly orchestral reductions) contain duplicate notes at the same onset and pitch. These are deduplicated by:

1. Identifying all (onset, pitch) pairs with multiple notes
2. Keeping the note with the longest duration
3. Recording all removed notes in metadata

### Note ID Assignment
Notes are assigned unique IDs by:
1. Sorting by onset time (ascending)
2. Breaking ties by MIDI pitch (descending, i.e., higher pitches first)
3. Assigning sequential integer IDs
