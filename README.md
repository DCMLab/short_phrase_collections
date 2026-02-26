# Short Phrase Reduction Stimuli

A curated collection of 8 short polyphonic phrases for music cognition experiments, specifically designed for iterative music reduction studies.

## Overview

This dataset contains musical excerpts used as stimuli in behavioral experiments investigating note-level structural salience in polyphonic music. Each phrase is selected to be:

- **Short**: 8-16 bars, suitable for iterative reduction tasks
- **Tonally coherent**: Begins and ends in the same key (or returns to tonic)
- **Structurally complete**: Contains clear phrase boundaries
- **Polyphonically rich**: Features multiple voices with melodic and harmonic content

## Dataset Structure

```
short_phrase_collections/
├── README.md
├── LICENSE
├── metadata/
│   └── phrases.csv          # Main metadata (single source of truth)
├── stimuli/
│   ├── phrase_01/           # Purcell - Rondeau from Abdelazer
│   │   ├── score.musicxml
│   │   └── score.pdf
│   ├── phrase_02/           # Handel - Suite HWV 450 Menuet
│   └── ...
└── docs/
    └── selection_criteria.md
```

## Phrases

| ID | Composer | Work | Key | Bars |
|----|----------|------|-----|------|
| phrase_01 | Purcell | Rondeau from Abdelazer | D minor | 1-8 |
| phrase_02 | Handel | Suite HWV 450 (Menuet) | G major | 1-8 |
| phrase_03 | Nardini | Adagio cantabile | A major | 1-8 |
| phrase_04 | Telemann | Gigue à l'Angloise | — | — |
| phrase_05 | Mozart | Piano Sonata K.331 | A major | 1-8 |
| phrase_06 | Corelli | Sarabande Op.5 No.7 | D minor | 1-16 |
| phrase_07 | Tartini | Violin Sonata (Devil's Trill) | G minor | — |
| phrase_08 | Haydn | Symphony No.88, 2nd mvt | D major | 1-8 |

## Note ID Convention

Each note in a stimulus file is assigned a unique ID following this traversal order:

1. Sort all notes by `offset` (onset time) ascending
2. For notes at the same offset, sort by `midi` pitch descending (higher pitch first)
3. Assign sequential IDs: `phrase_01_1`, `phrase_01_2`, ...

This ensures deterministic, reproducible ID assignment across processing pipelines.

## Deduplication

Some stimuli required preprocessing to remove duplicate notes (same onset + same pitch):

| Phrase | Notes Removed | Reason |
|--------|---------------|--------|
| phrase_03 (Nardini) | 4 | Notation artifacts |
| phrase_08 (Haydn) | 19 | Orchestral unison doublings in piano reduction |

**Policy**: When duplicates exist, the note with the longest duration is kept. Full details are recorded in `metadata/phrases.csv`.

## Usage

### Loading with music21 (Python)

```python
from music21 import converter

score = converter.parse('stimuli/phrase_01/score.musicxml')
for note in score.flatten().notes:
    print(note.pitch, note.offset, note.quarterLength)
```

### Metadata Access

```python
import pandas as pd

phrases = pd.read_csv('metadata/phrases.csv')
print(phrases[['phrase_id', 'composer', 'work_title', 'key']])
```

## Selection Criteria

See [docs/selection_criteria.md](docs/selection_criteria.md) for detailed inclusion/exclusion criteria.

## Citation

If you use this dataset, please cite:

```bibtex
@dataset{wang2025phrases,
  author = {Wang, Xiaoxuan},
  title = {Short Phrase Reduction Stimuli},
  year = {2025},
  publisher = {Digital and Cognitive Musicology Lab, EPFL},
  url = {https://github.com/DCMLab/short_phrase_collections}
}
```

## License

This dataset is released under [CC BY-SA 4.0](LICENSE).

The musical works included are in the public domain. Score encodings are derived from IMSLP sources.

## Contact

- Xiaoxuan Wang (xiaoxuan.wang@epfl.ch)
- Digital and Cognitive Musicology Lab, EPFL
