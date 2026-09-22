# Making Unpaired Drifting Work for Single-Step Speech Enhancement — code

Companion repository for the paper *"Unsupervised Speech Enhancement via Drifting"* (submitted to ICASSP 2027).

**Audio demo:** [d-caviedes.github.io/unpaired-drifting-se](https://d-caviedes.github.io/unpaired-drifting-se/) — the four external systems against our two headline systems on VoiceBank--DEMAND.

**Status: work in progress.** The full release is prepared and pending
internal open-source approval; it will appear here by camera-ready.

## What this repository will contain

- The drifting training engine (PyTorch) with the paper's two
  input-conditioning mechanisms: the **anchor** (input-derived positive
  target) and the **key** (input-conditioned reweighting of the clean bank),
  including the confidence-gated per-frame key strength.
- One recipe script per "ours" row of the paper's tables
  (denoising on VoiceBank–DEMAND, dereverberation on WSJ0-REVERB), each a
  single Hydra command with the exact hyperparameters.
- The self-paired corrector (second stage) training and application scripts.
- The evaluation pipeline used for every number in the paper: WER with
  deletion/insertion decomposition (wav2vec2-base-960h judge), speaker
  similarity (ECAPA), DNSMOS, SCOREQ, PESQ, STOI — complete test sets,
  externals rescored with the same ruler.
- Frame-bank precomputation from DNS-2020 clean speech, and the
  training-free encoder diagnostics of Table 1.

All frozen encoders are public (WavLM-base-plus, ECAPA-TDNN, DistilHuBERT,
wav2vec2-base-960h) and download automatically; the WavCube encoder used by
the denoising bank will be available from the authors on request. Datasets
are the public VoiceBank–DEMAND, WSJ0 (LDC) rendered with the SGMSE+
reverberation recipe, and DNS-2020 clean speech.

## Contact

Questions before the code lands: open an issue or contact the authors.
