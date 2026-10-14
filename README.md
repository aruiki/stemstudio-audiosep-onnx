# StemStudio AudioSep ONNX model

Fixed electric lead-guitar spectral-mask model for browser inference.

Source weights: https://huggingface.co/nielsr/audiosep-demo at revision 9188caa202a0d31845367e4dad8bb5549eddb4ba (publisher declares Apache-2.0). Official implementation: https://github.com/Audio-AGI/AudioSep, MIT (Copyright (c) Xubo Liu).

Changes: precompute the CLAP embedding for "Lead electric guitar playing a melody"; remove unused text/audio query encoder and STFT/ISTFT weights; export magnitude-to-mask network with fixed 5-second shape; store large weight initializers as float16 and cast to float32. Activations and I/O remain float32. No new training.

Input magnitude: float32 [1,1,501,1025], 32kHz, 2048-point periodic Hann, hop 320, centered reflect STFT of 160000 samples. Output features: float32 [1,3,501,1025], magnitude logits and real/imaginary phase-mask logits. Correct FFT reconstruction is required.

Model: audiosep-lead-mask.fp16w.onnx, 51,434,099 bytes. SHA-256 is in manifest.json. This experimental model is not guaranteed to separate every arrangement or acoustic guitar. A residual from a full mix can contain other instruments.

LICENSE retains Apache-2.0. AudioSep-code-MIT.txt retains the implementation notice. No user recordings or dataset audio are included.
