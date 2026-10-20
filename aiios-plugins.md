# AII OS Plugin Catalog

Signed packages for AII OS. The host verifies the index signature, package hash,
signed package metadata and compatibility before installation.

```json
{
  "catalog_version": 1,
  "generated": "2026-10-20T17:21:34Z",
  "must_understand": [
    "compat"
  ],
  "plugins": [
    {
      "id": "id.aeon.memory",
      "version": "0.8.2",
      "tier": "T3",
      "summary": "Task notes and reusable working lessons with explicit applicability and evidence references.",
      "description": "Store and retrieve notes through the host memory record. Search returns useful text, provenance, applicability and supersession status; a note remains working memory rather than permanent identity truth.",
      "publisher": "AI Identity Incorporated",
      "homepage": "https://github.com/aiii-dot-id/aeon-memory",
      "license": "Apache-2.0",
      "packages": [
        {
          "platform": "*",
          "arch": "*",
          "url": "https://github.com/aiii-dot-id/aeon-memory/releases/download/v0.8.2/id.aeon.memory-0.8.2.aiiospkg",
          "sha256": "sha256:191ba843371635c44fc5e71a5f5f8e3dbd3410a0428d0f4e9d55056603bc8a13",
          "size": 627243
        }
      ],
      "title": "Aeon Memory",
      "aiios_min_version": "0.1.20"
    },
    {
      "id": "id.aiii.voice",
      "version": "0.1.0-beta.11.4",
      "tier": "T3",
      "summary": "AII Voice",
      "packages": [
        {
          "platform": "linux",
          "arch": "x86_64",
          "url": "https://github.com/aiii-dot-id/aiios-voice-plugin/releases/download/v0.1.0-beta.11.4/id.aiii.voice-0.1.0-beta.11.4.aiiospkg",
          "sha256": "sha256:e7495a74d57be5d1c811d6fe80ed8bc1a70d8cbfc4250782820c6f5d2c895f76",
          "size": 25029773
        },
        {
          "platform": "macos",
          "arch": "arm64",
          "url": "https://github.com/aiii-dot-id/aiios-voice-plugin/releases/download/v0.1.0-beta.11.4/id.aiii.voice-0.1.0-beta.11.4.aiiospkg",
          "sha256": "sha256:e7495a74d57be5d1c811d6fe80ed8bc1a70d8cbfc4250782820c6f5d2c895f76",
          "size": 25029773,
          "os_min_version": "26.5"
        },
        {
          "platform": "windows",
          "arch": "x86_64",
          "url": "https://github.com/aiii-dot-id/aiios-voice-plugin/releases/download/v0.1.0-beta.11.4/id.aiii.voice-0.1.0-beta.11.4.aiiospkg",
          "sha256": "sha256:e7495a74d57be5d1c811d6fe80ed8bc1a70d8cbfc4250782820c6f5d2c895f76",
          "size": 25029773
        }
      ],
      "title": "AII Voice",
      "description": "Native speech recognition and synthesis: English recognition with a correction list the identity can teach, twenty selectable voices, seven speaking languages (a language other than English is downloaded when it is chosen), active voice-activity detection with an adjustable pause, interruption and recovery, and guided speaker enrollment and identification. One signed package selects the companion runtime and model data for macOS Apple Silicon, Ubuntu x86-64 or Windows x86-64. AII OS owns downloads, integrity verification, installation, audio, permissions and updates; no system Python is required. Desktop beta: recognition is English only. Speaker identification is probabilistic evidence, not authentication. Read the release notes for prerequisites, settings and qualification limits. Third-party model and runtime components retain their own licenses.",
      "publisher": "AI Identity Incorporated",
      "homepage": "https://github.com/aiii-dot-id/aiios-voice-plugin",
      "license": "Apache-2.0",
      "category": "voice",
      "keywords": [
        "speech",
        "voice",
        "STT",
        "TTS",
        "VAD",
        "speaker identification"
      ],
      "aiios_min_version": "0.1.15"
    },
    {
      "id": "id.aiii.codequality",
      "version": "0.1.13",
      "tier": "T3",
      "summary": "Review source code and comments for quality findings and dimension scores.",
      "description": "Review supplied text or scan a sandboxed folder in bounded batches. Results include located findings where available, dimension scores and coverage limits.",
      "publisher": "AI Identity Incorporated",
      "homepage": "https://github.com/aiii-dot-id/aii-codequality-plugin",
      "license": "Apache-2.0",
      "category": "code quality",
      "keywords": [
        "code quality",
        "code review",
        "maintainability",
        "Jev",
        "scan"
      ],
      "packages": [
        {
          "platform": "*",
          "arch": "*",
          "url": "https://github.com/aiii-dot-id/aii-codequality-plugin/releases/download/v0.1.13/id.aiii.codequality-0.1.13.aiiospkg",
          "sha256": "sha256:e6304d474a6bab71041f05ecf3b138ef1ac948379edaa975b5e3b2626927801b",
          "size": 1643126
        }
      ],
      "title": "Code Quality",
      "aiios_min_version": "0.1.10"
    },
    {
      "id": "id.aiii.jev",
      "title": "Jev",
      "version": "0.1.2",
      "tier": "T3",
      "publisher": "AI Identity Incorporated",
      "homepage": "https://github.com/aiii-dot-id/aiios-jev-plugin",
      "license": "Apache-2.0",
      "summary": "Evaluate text against explicit questions and a chosen judgment model.",
      "description": "Run bounded text judgments with explicit questions, model selection and structured results. Model judgments are evidence to assess, not independent verification.",
      "aiios_min_version": "0.1.10",
      "packages": [
        {
          "platform": "*",
          "arch": "*",
          "url": "https://github.com/aiii-dot-id/aiios-jev-plugin/releases/download/v0.1.2/id.aiii.jev-0.1.2.aiiospkg",
          "sha256": "sha256:3cd98b4690ae2bda0570b1eff605be15122e7d37d54ba8a23df3369c94ec73e5",
          "size": 486838
        }
      ]
    },
    {
      "id": "id.aeon.planning",
      "title": "Planning",
      "version": "0.8.2",
      "tier": "T3",
      "publisher": "AI Identity Incorporated",
      "homepage": "https://github.com/aiii-dot-id/aiios-planning-plugin",
      "license": "Apache-2.0",
      "summary": "Review task plans, recorded tool calls, execution outcomes and returned evidence.",
      "description": "Read the current work plan and review a work session with its descendants. Counts and excerpts declare coverage and unavailable evidence. Execution success is distinct from task correctness; explicit calibration and abandonment remain available.",
      "aiios_min_version": "0.1.19",
      "packages": [
        {
          "platform": "linux",
          "arch": "x86_64",
          "url": "https://github.com/aiii-dot-id/aiios-planning-plugin/releases/download/v0.8.2/id.aeon.planning-0.8.2.aiiospkg",
          "sha256": "sha256:cedcd74511361bc0b2ff14427d7398a3572b3cba6433a292c2362944d8cafa83",
          "size": 2816957
        },
        {
          "platform": "macos",
          "arch": "arm64",
          "url": "https://github.com/aiii-dot-id/aiios-planning-plugin/releases/download/v0.8.2/id.aeon.planning-0.8.2.aiiospkg",
          "sha256": "sha256:cedcd74511361bc0b2ff14427d7398a3572b3cba6433a292c2362944d8cafa83",
          "size": 2816957
        }
      ]
    },
    {
      "id": "id.aiii.meaning",
      "version": "0.0.1-beta.6",
      "tier": "T3",
      "summary": "AII Meaning",
      "aiios_min_version": "0.1.15",
      "packages": [
        {
          "platform": "macos",
          "arch": "arm64",
          "os_min_version": "26.5",
          "url": "https://github.com/aiii-dot-id/aiios-meaning-plugin/releases/download/v0.0.1-beta.6/id.aiii.meaning-0.0.1-beta.6.aiiospkg",
          "sha256": "sha256:6dd36476e3cf2f2dbcd51f2f4181fdaecd9cdf47be32831a9f85b1c1fd832d9c",
          "size": 5526924
        },
        {
          "platform": "linux",
          "arch": "x86_64",
          "url": "https://github.com/aiii-dot-id/aiios-meaning-plugin/releases/download/v0.0.1-beta.6/id.aiii.meaning-0.0.1-beta.6.aiiospkg",
          "sha256": "sha256:6dd36476e3cf2f2dbcd51f2f4181fdaecd9cdf47be32831a9f85b1c1fd832d9c",
          "size": 5526924
        },
        {
          "platform": "linux",
          "arch": "arm64",
          "url": "https://github.com/aiii-dot-id/aiios-meaning-plugin/releases/download/v0.0.1-beta.6/id.aiii.meaning-0.0.1-beta.6.aiiospkg",
          "sha256": "sha256:6dd36476e3cf2f2dbcd51f2f4181fdaecd9cdf47be32831a9f85b1c1fd832d9c",
          "size": 5526924
        },
        {
          "platform": "windows",
          "arch": "x86_64",
          "url": "https://github.com/aiii-dot-id/aiios-meaning-plugin/releases/download/v0.0.1-beta.6/id.aiii.meaning-0.0.1-beta.6.aiiospkg",
          "sha256": "sha256:6dd36476e3cf2f2dbcd51f2f4181fdaecd9cdf47be32831a9f85b1c1fd832d9c",
          "size": 5526924
        }
      ],
      "title": "AII Meaning",
      "description": "Recall by meaning, computed on this machine. Turns a memory or a cue into a vector with a multilingual embedding model, so that the identity's recall finds what is near in sense as well as what shares words. Only AII OS asks it: it has no network, no tools, no settings and no storage, and keeps nothing it is handed. One signed package for macOS Apple Silicon, Linux x86-64, Linux arm64 and Windows x86-64; AII OS downloads the model and its tokenizer (328 MB) and the runtime for its own platform and verifies each. It computes on the processor, on four threads at most, and lets the model go from memory a minute after the last recall; an AII OS that offers it lets the operator choose fewer threads and how long the model is kept. A memory is read to its first 2,048 tokens: the whole of an 8,000-character entry in English, German or Spanish, and about the first 3,900 characters of Korean, 3,450 of Japanese and 2,900 of Chinese; what lies after that in a long entry is not read. Third-party model and runtime components retain their own licenses.",
      "publisher": "AI Identity Incorporated",
      "homepage": "https://github.com/aiii-dot-id/aiios-meaning-plugin",
      "license": "Apache-2.0",
      "category": "memory",
      "keywords": [
        "memory",
        "recall",
        "embeddings",
        "meaning",
        "semantic search"
      ]
    }
  ]
}
```
