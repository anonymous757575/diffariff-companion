<link rel="stylesheet" href="https://cdn.jsdelivr.net/npm/katex@0.10.2/dist/katex.min.css" integrity="sha384-yFRtMMDnQtDRO8rLpMIKrtPCD5jdktao2TV19YiZYWMDkUR5GQZR/NOVTdquEx1j" crossorigin="anonymous">
<script defer src="https://cdn.jsdelivr.net/npm/katex@0.10.2/dist/katex.min.js" integrity="sha384-9Nhn55MVVN0/4OFx7EE5kpFBPsEMZxKTCnA+4fqDmg12eCTqGi6+BB2LjY8brQxJ" crossorigin="anonymous"></script>
<script defer src="https://cdn.jsdelivr.net/npm/katex@0.10.2/dist/contrib/auto-render.min.js" integrity="sha384-kWPLUVMOks5AQFrykwIup5lo0m3iMkkHrD0uJ4H5cjeGihAutqP0yW0J6dpFiVkI" crossorigin="anonymous" onload="renderMathInElement(document.body);"></script>

<style>
audio{
  width:200px;
  height:40px;
}
audio::-webkit-media-controls-timeline,
audio::-webkit-media-controls-seek-back-button,
audio::-webkit-media-controls-seek-forward-button {
  display: none !important;
}
</style>


# Diff-A-Riff: Musical Accompaniment Co-creation via Latent Diffusion Models

**This website is a work in progress that will be completed by April 24th.**

This is the accompanying website to "Diff-a-Riff: Musical Accompaniment Co-creation via Latent Diffusion Models" submitted to ISMIR 2024.

  * [System's Overview](#systems-overview)
  * [Sound Examples](#sound-examples)
    + [Accompaniment Generation : a context is provided](#accompaniment-generation--a-context-is-provided)
      - [Context-only, no CLAP](#context-only-no-clap)
      - [With Text CLAP](#with-text-clap)
      - [With Audio CLAP](#with-audio-clap)
      - [Complete Music Excerpts](#complete-music-excerpts)
    + [Single Track generation : no context is provided](#single-track-generation--no-context-is-provided)
      - [Fully Unconditional](#fully-unconditional)
      - [With Text CLAP](#with-text-clap-1)
      - [With Audio CLAP](#with-audio-clap-1)
    + [Bonus](#bonus)
      - [Inpainting](#inpainting)
      - [Interpolations](#interpolations)
      - [Variations](#variations)
      - [Stereo width](#stereo-width)
      - [Loop Sampling](#loop-sampling)
  * [User Study Sample Questions](#user-study-sample-questions)
    + [Audio Quality Assessment](#audio-quality-assessment)
    + [Subjective Audio Prompt Adherence](#subjective-audio-prompt-adherence)
  * [References](#references)

## System's Overview 
<!-- ![Overview of Diff-A-Riff](https://anonymous757575.github.io/diffariff-companion/diff-a-riff-website.png "Title") -->

<figure>
  <img src="https://anonymous757575.github.io/diffariff-companion/diff-a-riff-website.png" alt="Overview of Diff-A-Riff"/>
  <figcaption> <b>Overview of Diff-A-Riff.</b> The CAE Encoder transforms the music context into a compressed representation, concatenated with a noisy sample, and further processed through the multi-scale U-Net. The generated latent sequence is decoded into audio via the CAE Decoder. We highlight frozen components in blue and trainable elements in orange. At inference time, the conditioning signals are optional and one can try different conditional setups.</figcaption>
</figure>

Here, I would add a reminder for the notation, and use it later 
$$\textit{CLAP}_\text{Audio}$$, $$\textit{CLAP}_\text{Text}$$ and $$\textit{Context}$$
Maybe rewrite the caption to focus on inference. Maybe remove the training-related stuff in the fig ? 

## Sound Examples
In this section, we demonstrate the generation abilities of our model under different conditioning signals.

### Accompaniment Generation : a context is provided
In this section, we demonstrate the ability of Diff-A-Riff to generate accompaniments, single tracks that fit a pre-existing context.

#### Context-only, no CLAP
The model can generate accompaniments from a context only, without the need for CLAP embeddings.

<table class="tg">
<thead>
  <tr>
    <th class="tg-0pky">Context</th>
    <th class="tg-0pky" colspan="4">Accompaniments</th>
  </tr>
</thead>
<tbody>
  <tr>
    <td class="tg-0pky"> <audio controls controlsList="nodownload"><source src="https://anonymous757575.github.io/diffariff-companion/audios/context-only/1/context.wav" type="audio/wav"> Your Browser does not support the audio tag </audio> </td>
    <td class="tg-0pky"> <audio controls controlsList="nodownload"><source src="https://anonymous757575.github.io/diffariff-companion/audios/context-only/1/gen1_mix.wav" type="audio/wav"> Your Browser does not support the audio tag </audio> </td>
    <td class="tg-0pky"> <audio controls controlsList="nodownload"><source src="https://anonymous757575.github.io/diffariff-companion/audios/context-only/1/gen2_mix.wav" type="audio/wav"> Your Browser does not support the audio tag </audio> </td>
    <td class="tg-0pky"> <audio controls controlsList="nodownload"><source src="https://anonymous757575.github.io/diffariff-companion/audios/context-only/1/gen3_mix.wav" type="audio/wav"> Your Browser does not support the audio tag </audio> </td>
    <td class="tg-0pky"> <audio controls controlsList="nodownload"><source src="https://anonymous757575.github.io/diffariff-companion/audios/context-only/1/gen4_mix.wav" type="audio/wav"> Your Browser does not support the audio tag </audio> </td>
  </tr>
  <tr>
    <td class="tg-0pky"> <audio controls controlsList="nodownload"><source src="https://anonymous757575.github.io/diffariff-companion/audios/context-only/2/context.mp3" type="audio/mp3"> Your Browser does not support the audio tag </audio> </td>
    <td class="tg-0pky"> <audio controls controlsList="nodownload"><source src="https://anonymous757575.github.io/diffariff-companion/audios/context-only/2/gen1_mix.wav" type="audio/wav"> Your Browser does not support the audio tag </audio> </td>
    <td class="tg-0pky"> <audio controls controlsList="nodownload"><source src="https://anonymous757575.github.io/diffariff-companion/audios/context-only/2/gen2_mix.wav" type="audio/wav"> Your Browser does not support the audio tag </audio> </td>
    <td class="tg-0pky"> <audio controls controlsList="nodownload"><source src="https://anonymous757575.github.io/diffariff-companion/audios/context-only/2/gen3_mix.wav" type="audio/wav"> Your Browser does not support the audio tag </audio> </td>
  </tr>
  <tr>
    <td class="tg-0pky"> <audio controls controlsList="nodownload"><source src="https://anonymous757575.github.io/diffariff-companion/audios/context-only/3/context.wav" type="audio/wav"> Your Browser does not support the audio tag </audio> </td>
    <td class="tg-0pky"> <audio controls controlsList="nodownload"><source src="https://anonymous757575.github.io/diffariff-companion/audios/context-only/3/gen5_mix.wav" type="audio/wav"> Your Browser does not support the audio tag </audio> </td>
    <td class="tg-0pky"> <audio controls controlsList="nodownload"><source src="https://anonymous757575.github.io/diffariff-companion/audios/context-only/3/gen2_mix.wav" type="audio/wav"> Your Browser does not support the audio tag </audio> </td>
    <td class="tg-0pky"> <audio controls controlsList="nodownload"><source src="https://anonymous757575.github.io/diffariff-companion/audios/context-only/3/gen3_mix.wav" type="audio/wav"> Your Browser does not support the audio tag </audio> </td>
    <td class="tg-0pky"> <audio controls controlsList="nodownload"><source src="https://anonymous757575.github.io/diffariff-companion/audios/context-only/3/gen4_mix.wav" type="audio/wav"> Your Browser does not support the audio tag </audio> </td>
    <td class="tg-0pky"> <audio controls controlsList="nodownload"><source src="https://anonymous757575.github.io/diffariff-companion/audios/context-only/3/gen1_mix.wav" type="audio/wav"> Your Browser does not support the audio tag </audio> </td>
  </tr>  
  <tr>
    <td class="tg-0pky"> <audio controls controlsList="nodownload"><source src="https://anonymous757575.github.io/diffariff-companion/audios/context-only/4/context.wav" type="audio/wav"> Your Browser does not support the audio tag </audio> </td>
    <td class="tg-0pky"> <audio controls controlsList="nodownload"><source src="https://anonymous757575.github.io/diffariff-companion/audios/context-only/4/gen1_mix.wav" type="audio/wav"> Your Browser does not support the audio tag </audio> </td>
    <td class="tg-0pky"> <audio controls controlsList="nodownload"><source src="https://anonymous757575.github.io/diffariff-companion/audios/context-only/4/gen2_mix.wav" type="audio/wav"> Your Browser does not support the audio tag </audio> </td>
    <td class="tg-0pky"> <audio controls controlsList="nodownload"><source src="https://anonymous757575.github.io/diffariff-companion/audios/context-only/4/gen3_mix.wav" type="audio/wav"> Your Browser does not support the audio tag </audio> </td>
    <td class="tg-0pky"> <audio controls controlsList="nodownload"><source src="https://anonymous757575.github.io/diffariff-companion/audios/context-only/4/gen4_mix.wav" type="audio/wav"> Your Browser does not support the audio tag </audio> </td>
  </tr>
</tbody>
</table>

#### With Text CLAP
Given a context music piece, Diff-A-Riff allows to specify the accompaniment using a text prompt. Here, we present various context music pieces and various text-based accompaniments.

<table class="tg">
<thead>
  <tr>
    <th class="tg-0pky">Context</th>
    <th class="tg-0pky">Text Prompt</th>
    <th class="tg-0lax" colspan="3">Accompaniments</th>
  </tr>
</thead>
<tbody>
  <tr>
    <td class="tg-0pky" rowspan="2"> <audio controls controlsList="nodownload"><source src="https://anonymous757575.github.io/diffariff-companion/audios/text-cond/context/1/context.mp3" type="audio/mp3"> Your Browser does not support the audio tag </audio> </td>
    <td class="tg-0pky">"A solo ukulele delivering a cheerful and sunny accompaniment."</td>
    <td class="tg-0lax"> <audio controls controlsList="nodownload"><source src="https://anonymous757575.github.io/diffariff-companion/audios/text-cond/context/1/prompt1/gen1_mix_vol.wav"> Your Browser does not support the audio tag </audio> </td>
    <td class="tg-0lax"> <audio controls controlsList="nodownload"><source src="https://anonymous757575.github.io/diffariff-companion/audios/text-cond/context/1/prompt1/gen2_mix_vol.wav"> Your Browser does not support the audio tag </audio> </td>
  </tr>
  <tr>
    <td class="tg-0pky">"A mellow synthesizer playing ethereal pads."</td>
    <td class="tg-0lax"> <audio controls controlsList="nodownload"><source src="https://anonymous757575.github.io/diffariff-companion/audios/text-cond/context/1/prompt2/gen1_mix_vol.wav" type="audio/wav"> Your Browser does not support the audio tag </audio> </td>
    <td class="tg-0pky"> <audio controls controlsList="nodownload"><source src="https://anonymous757575.github.io/diffariff-companion/audios/text-cond/context/1/prompt2/gen2_mix_vol.wav" type="audio/wav"> Your Browser does not support the audio tag </audio> </td>
  </tr>
  <tr>
    <td class="tg-0pky" rowspan="2"> <audio controls controlsList="nodownload"><source src="https://anonymous757575.github.io/diffariff-companion/audios/text-cond/context/2/context.mp3" type="audio/wav"> Your Browser does not support the audio tag </audio> </td>
    <td class="tg-0pky">"Drums with reverb and a lot of toms."</td>
    <td class="tg-0lax"> <audio controls controlsList="nodownload"><source src="https://anonymous757575.github.io/diffariff-companion/audios/text-cond/context/2/prompt1/gen1_mix_vol.wav"> Your Browser does not support the audio tag </audio> </td>
    <td class="tg-0lax"> <audio controls controlsList="nodownload"><source src="https://anonymous757575.github.io/diffariff-companion/audios/text-cond/context/2/prompt1/gen2_mix_vol.wav"> Your Browser does not support the audio tag </audio> </td>
  </tr>
  <tr>
    <td class="tg-0pky">"Drums with reverb and a lot of soft hats."</td>
    <td class="tg-0lax"> <audio controls controlsList="nodownload"><source src="https://anonymous757575.github.io/diffariff-companion/audios/text-cond/context/2/prompt2/gen1_mix_vol.wav" type="audio/wav"> Your Browser does not support the audio tag </audio> </td>
    <td class="tg-0pky"> <audio controls controlsList="nodownload"><source src="https://anonymous757575.github.io/diffariff-companion/audios/text-cond/context/2/prompt2/gen2_mix_vol.wav" type="audio/wav"> Your Browser does not support the audio tag </audio> </td>
  </tr>
</tbody>
</table>

#### With Audio CLAP
Given a context music piece, Diff-A-Riff allows the generation of accompaniments based on an audio reference. Here, we present various context music pieces and various audio-based accompaniments.

<table class="tg">
<thead>
  <tr>
    <th class="tg-0pky">Context</th>
    <th class="tg-0pky">Audio Reference</th>
    <th class="tg-0lax" colspan="3">Accompaniments</th>
  </tr>
</thead>
<tbody>
  <tr>
    <td class="tg-0pky" rowspan="2"> <audio controls controlsList="nodownload"><source src="https://anonymous757575.github.io/diffariff-companion/audios/audio-cond/context/1/context.mp3" type="audio/mp3"> Your Browser does not support the audio tag </audio> </td>
    <td class="tg-0pky"> <audio controls controlsList="nodownload"><source src="https://anonymous757575.github.io/diffariff-companion/audios/audio-cond/context/1/ref1/ref.wav" type="audio/wav"> Your Browser does not support the audio tag </audio> </td>
    <td class="tg-0lax"> <audio controls controlsList="nodownload"><source src="https://anonymous757575.github.io/diffariff-companion/audios/audio-cond/context/1/ref1/gen1_mix.wav" type="audio/wav"> Your Browser does not support the audio tag </audio> </td>
    <td class="tg-0pky"> <audio controls controlsList="nodownload"><source src="https://anonymous757575.github.io/diffariff-companion/audios/audio-cond/context/1/ref1/gen2_mix.wav" type="audio/wav"> Your Browser does not support the audio tag </audio> </td>
  </tr>
  <tr>
    <td class="tg-0pky"> <audio controls controlsList="nodownload"><source src="https://anonymous757575.github.io/diffariff-companion/audios/audio-cond/context/1/ref2/ref.wav" type="audio/wav"> Your Browser does not support the audio tag </audio> </td>
    <td class="tg-0lax"> <audio controls controlsList="nodownload"><source src="https://anonymous757575.github.io/diffariff-companion/audios/audio-cond/context/1/ref2/gen1_mix.wav" type="audio/wav"> Your Browser does not support the audio tag </audio> </td>
    <td class="tg-0pky"> <audio controls controlsList="nodownload"><source src="https://anonymous757575.github.io/diffariff-companion/audios/audio-cond/context/1/ref2/gen2_mix.wav" type="audio/wav"> Your Browser does not support the audio tag </audio> </td>
  </tr>
  <tr>
    <td class="tg-0pky" rowspan="2"> <audio controls controlsList="nodownload"><source src="https://anonymous757575.github.io/diffariff-companion/audios/audio-cond/context/2/context.mp3" type="audio/mp3"> Your Browser does not support the audio tag </audio> </td>
    <td class="tg-0pky"> <audio controls controlsList="nodownload"><source src="https://anonymous757575.github.io/diffariff-companion/audios/audio-cond/context/2/ref1/ref.wav" type="audio/wav"> Your Browser does not support the audio tag </audio> </td>
    <td class="tg-0lax"> <audio controls controlsList="nodownload"><source src="https://anonymous757575.github.io/diffariff-companion/audios/audio-cond/context/2/ref1/gen1_mix.wav" type="audio/wav"> Your Browser does not support the audio tag </audio> </td>
    <td class="tg-0pky"> <audio controls controlsList="nodownload"><source src="https://anonymous757575.github.io/diffariff-companion/audios/audio-cond/context/2/ref1/gen2_mix.wav" type="audio/wav"> Your Browser does not support the audio tag </audio> </td>
  </tr>
  <tr>
    <td class="tg-0pky"> <audio controls controlsList="nodownload"><source src="https://anonymous757575.github.io/diffariff-companion/audios/audio-cond/context/2/ref2/ref.wav" type="audio/wav"> Your Browser does not support the audio tag </audio> </td>
    <td class="tg-0lax"> <audio controls controlsList="nodownload"><source src="https://anonymous757575.github.io/diffariff-companion/audios/audio-cond/context/2/ref2/gen1_mix.wav" type="audio/wav"> Your Browser does not support the audio tag </audio> </td>
    <td class="tg-0pky"> <audio controls controlsList="nodownload"><source src="https://anonymous757575.github.io/diffariff-companion/audios/audio-cond/context/2/ref2/gen2_mix.wav" type="audio/wav"> Your Browser does not support the audio tag </audio> </td>
  </tr>
</tbody>
</table>

#### Complete Music Excerpts
Using an iterative mechanism where we generate tracks and sum them to constitute a context for the next iteration, we are able to generate multi track music pieces from Diff-A-Riff. Here you can find excerpts of multitrack music generated this way.

<table class="tg">
<tbody>
  <tr>
    <td class="tg-0pky"> <audio controls controlsList="nodownload"><source src="https://anonymous757575.github.io/diffariff-companion/audios/full/track_1.wav" type="audio/wav"> Your Browser does not support the audio tag </audio> </td>
    <td class="tg-0pky"> <audio controls controlsList="nodownload"><source src="https://anonymous757575.github.io/diffariff-companion/audios/full/track_2.wav" type="audio/wav"> Your Browser does not support the audio tag </audio> </td>
    <td class="tg-0pky"> <audio controls controlsList="nodownload"><source src="https://anonymous757575.github.io/diffariff-companion/audios/full/track_3.wav" type="audio/wav"> Your Browser does not support the audio tag </audio> </td>
  </tr>
  <tr>
    <td class="tg-0pky"> <audio controls controlsList="nodownload"><source src="https://anonymous757575.github.io/diffariff-companion/audios/full/track_4.wav" type="audio/wav"> Your Browser does not support the audio tag </audio> </td>
    <td class="tg-0pky"> <audio controls controlsList="nodownload"><source src="https://anonymous757575.github.io/diffariff-companion/audios/full/track_5.wav" type="audio/wav"> Your Browser does not support the audio tag </audio> </td>
    <td class="tg-0pky"> <audio controls controlsList="nodownload"><source src="https://anonymous757575.github.io/diffariff-companion/audios/full/track_6.wav" type="audio/wav"> Your Browser does not support the audio tag </audio> </td>
  </tr>
  <tr>
    <td class="tg-0pky"> <audio controls controlsList="nodownload"><source src="https://anonymous757575.github.io/diffariff-companion/audios/full/track_7.wav" type="audio/wav"> Your Browser does not support the audio tag </audio> </td>
    <td class="tg-0pky"> <audio controls controlsList="nodownload"><source src="https://anonymous757575.github.io/diffariff-companion/audios/full/track_8.wav" type="audio/wav"> Your Browser does not support the audio tag </audio> </td>
    <td class="tg-0pky"> <audio controls controlsList="nodownload"><source src="https://anonymous757575.github.io/diffariff-companion/audios/full/track_9.wav" type="audio/wav"> Your Browser does not support the audio tag </audio> </td>
  </tr>

  <tr>
    <td class="tg-0pky"> <audio controls controlsList="nodownload"><source src="https://anonymous757575.github.io/diffariff-companion/audios/full/track_10.wav" type="audio/wav"> Your Browser does not support the audio tag </audio> </td>
    <td class="tg-0pky"> <audio controls controlsList="nodownload"><source src="https://anonymous757575.github.io/diffariff-companion/audios/full/track_11.wav" type="audio/wav"> Your Browser does not support the audio tag </audio> </td>
    <td class="tg-0pky"> <audio controls controlsList="nodownload"><source src="https://anonymous757575.github.io/diffariff-companion/audios/full/track_12.wav" type="audio/wav"> Your Browser does not support the audio tag </audio> </td>
  </tr>
 
</tbody>
</table>



### Single Track generation : no context is provided
Diff-A-Riff also allows the generation of solo instrument tracks without a context. We then refer to it as single track generation, rather than accompaniment.

#### Fully Unconditional
In this section, we show clips generated without context or CLAP conditioning.
<table class="tg">
<tbody>
  <tr>
    <td class="tg-0pky"> <audio controls controlsList="nodownload"><source src="https://anonymous757575.github.io/diffariff-companion/audios/uncond/gen.wav" type="audio/wav"> Your Browser does not support the audio tag </audio> </td>
    <td class="tg-0pky"> <audio controls controlsList="nodownload"><source src="https://anonymous757575.github.io/diffariff-companion/audios/uncond/gen1.wav" type="audio/wav"> Your Browser does not support the audio tag </audio> </td>
    <td class="tg-0pky"> <audio controls controlsList="nodownload"><source src="https://anonymous757575.github.io/diffariff-companion/audios/uncond/gen2.wav" type="audio/wav"> Your Browser does not support the audio tag </audio> </td>
  </tr>
  <tr>
    <td class="tg-0pky"> <audio controls controlsList="nodownload"><source src="https://anonymous757575.github.io/diffariff-companion/audios/uncond/gen3.wav" type="audio/wav"> Your Browser does not support the audio tag </audio> </td>
    <td class="tg-0pky"> <audio controls controlsList="nodownload"><source src="https://anonymous757575.github.io/diffariff-companion/audios/uncond/gen4.wav" type="audio/wav"> Your Browser does not support the audio tag </audio> </td>
    <td class="tg-0pky"> <audio controls controlsList="nodownload"><source src="https://anonymous757575.github.io/diffariff-companion/audios/uncond/gen5.wav" type="audio/wav"> Your Browser does not support the audio tag </audio> </td>
  </tr>
  <tr>
    <td class="tg-0pky"> <audio controls controlsList="nodownload"><source src="https://anonymous757575.github.io/diffariff-companion/audios/uncond/gen6.wav" type="audio/wav"> Your Browser does not support the audio tag </audio> </td>
    <td class="tg-0pky"> <audio controls controlsList="nodownload"><source src="https://anonymous757575.github.io/diffariff-companion/audios/uncond/gen7.wav" type="audio/wav"> Your Browser does not support the audio tag </audio> </td>
    <td class="tg-0pky"> <audio controls controlsList="nodownload"><source src="https://anonymous757575.github.io/diffariff-companion/audios/uncond/gen8.wav" type="audio/wav"> Your Browser does not support the audio tag </audio> </td>
  </tr>

  <tr>
    <td class="tg-0pky"> <audio controls controlsList="nodownload"><source src="https://anonymous757575.github.io/diffariff-companion/audios/uncond/gen9.wav" type="audio/wav"> Your Browser does not support the audio tag </audio> </td>
    <td class="tg-0pky"> <audio controls controlsList="nodownload"><source src="https://anonymous757575.github.io/diffariff-companion/audios/uncond/gen10.wav" type="audio/wav"> Your Browser does not support the audio tag </audio> </td>
    <td class="tg-0pky"> <audio controls controlsList="nodownload"><source src="https://anonymous757575.github.io/diffariff-companion/audios/uncond/gen11.wav" type="audio/wav"> Your Browser does not support the audio tag </audio> </td>
  </tr>
  <tr>
    <td class="tg-0pky"> <audio controls controlsList="nodownload"><source src="https://anonymous757575.github.io/diffariff-companion/audios/uncond/gen12.wav" type="audio/wav"> Your Browser does not support the audio tag </audio> </td>
    <td class="tg-0pky"> <audio controls controlsList="nodownload"><source src="https://anonymous757575.github.io/diffariff-companion/audios/uncond/gen13.wav" type="audio/wav"> Your Browser does not support the audio tag </audio> </td>
    <td class="tg-0pky"> <audio controls controlsList="nodownload"><source src="https://anonymous757575.github.io/diffariff-companion/audios/uncond/gen14.wav" type="audio/wav"> Your Browser does not support the audio tag </audio> </td>
  </tr>
  
</tbody>
</table>

#### With Text CLAP
In this section, you can hear single instrument tracks generated solely from a text prompt

<table class="tg">
<thead>
  <tr>
    <th class="tg-0pky">Text Prompt</th>
    <th class="tg-0lax" colspan="3">Generations</th>
  </tr>
</thead>
<tbody>
  <tr>
    <td class="tg-0pky">"Guitar played folk style."</td>
    <td class="tg-0lax"> <audio controls controlsList="nodownload"><source src="https://anonymous757575.github.io/diffariff-companion/audios/text-cond/no-context/1/gen1.wav" type="audio/wav"> Your Browser does not support the audio tag </audio> </td>
    <td class="tg-0pky"> <audio controls controlsList="nodownload"><source src="https://anonymous757575.github.io/diffariff-companion/audios/text-cond/no-context/1/gen2.wav" type="audio/wav"> Your Browser does not support the audio tag </audio> </td>
  </tr>
    <tr>
    <td class="tg-0pky">"Slow evolving pad synth."</td>
    <td class="tg-0lax"> <audio controls controlsList="nodownload"><source src="https://anonymous757575.github.io/diffariff-companion/audios/text-cond/no-context/2/gen1.wav" type="audio/wav"> Your Browser does not support the audio tag </audio> </td>
    <td class="tg-0pky"> <audio controls controlsList="nodownload"><source src="https://anonymous757575.github.io/diffariff-companion/audios/text-cond/no-context/2/gen2.wav" type="audio/wav"> Your Browser does not support the audio tag </audio> </td>
  </tr>
  </tr>
    <tr>
    <td class="tg-0pky">"A vibrant, funky bassline characterized by the electrifying slap technique, where each note pops with a distinct rhythmic snap and sizzle."</td>
    <td class="tg-0lax"> <audio controls controlsList="nodownload"><source src="https://anonymous757575.github.io/diffariff-companion/audios/text-cond/no-context/3/gen1.wav" type="audio/wav"> Your Browser does not support the audio tag </audio> </td>
    <td class="tg-0pky"> <audio controls controlsList="nodownload"><source src="https://anonymous757575.github.io/diffariff-companion/audios/text-cond/no-context/3/gen2.wav" type="audio/wav"> Your Browser does not support the audio tag </audio> </td>
  </tr>
  </tr>
    <tr>
    <td class="tg-0pky">"A pulsating techno drum beat, where a deep bass kick thunders every quarter note, creating a relentless and hypnotic pulse."</td>
    <td class="tg-0lax"> <audio controls controlsList="nodownload"><source src="https://anonymous757575.github.io/diffariff-companion/audios/text-cond/no-context/4/gen1.wav" type="audio/wav"> Your Browser does not support the audio tag </audio> </td>
    <td class="tg-0pky"> <audio controls controlsList="nodownload"><source src="https://anonymous757575.github.io/diffariff-companion/audios/text-cond/no-context/4/gen2.wav" type="audio/wav"> Your Browser does not support the audio tag </audio> </td>
  </tr>
</tbody>
</table>

#### With Audio CLAP
Diff-A-Riff also allows the generation of solo instrument tracks conditioned on audio only.
<table class="tg">
<thead>
  <tr>
    <th class="tg-0pky">Audio Reference</th>
    <th class="tg-0lax" colspan="3">Generations</th>
  </tr>
</thead>
<tbody>
  <tr>
    <td class="tg-0pky"> <audio controls controlsList="nodownload"><source src="https://anonymous757575.github.io/diffariff-companion/audios/audio-cond/no-context/1/ref.wav" type="audio/wav"> Your Browser does not support the audio tag </audio> </td>
    <td class="tg-0lax"> <audio controls controlsList="nodownload"><source src="https://anonymous757575.github.io/diffariff-companion/audios/audio-cond/no-context/1/gen1.wav" type="audio/wav"> Your Browser does not support the audio tag </audio> </td>
    <td class="tg-0pky"> <audio controls controlsList="nodownload"><source src="https://anonymous757575.github.io/diffariff-companion/audios/audio-cond/no-context/1/gen2.wav" type="audio/wav"> Your Browser does not support the audio tag </audio> </td>
    <td class="tg-0pky"> <audio controls controlsList="nodownload"><source src="https://anonymous757575.github.io/diffariff-companion/audios/audio-cond/no-context/1/gen3.wav" type="audio/wav"> Your Browser does not support the audio tag </audio> </td>
  </tr>
  <tr>
    <td class="tg-0pky"> <audio controls controlsList="nodownload"><source src="https://anonymous757575.github.io/diffariff-companion/audios/audio-cond/no-context/2/ref.wav" type="audio/wav"> Your Browser does not support the audio tag </audio> </td>
    <td class="tg-0lax"> <audio controls controlsList="nodownload"><source src="https://anonymous757575.github.io/diffariff-companion/audios/audio-cond/no-context/2/gen1.wav" type="audio/wav"> Your Browser does not support the audio tag </audio> </td>
    <td class="tg-0pky"> <audio controls controlsList="nodownload"><source src="https://anonymous757575.github.io/diffariff-companion/audios/audio-cond/no-context/2/gen2.wav" type="audio/wav"> Your Browser does not support the audio tag </audio> </td>
    <td class="tg-0pky"> <audio controls controlsList="nodownload"><source src="https://anonymous757575.github.io/diffariff-companion/audios/audio-cond/no-context/2/gen3.wav" type="audio/wav"> Your Browser does not support the audio tag </audio> </td>
  </tr>
  <tr>
    <td class="tg-0pky"> <audio controls controlsList="nodownload"><source src="https://anonymous757575.github.io/diffariff-companion/audios/audio-cond/no-context/3/ref.wav" type="audio/wav"> Your Browser does not support the audio tag </audio> </td>
    <td class="tg-0lax"> <audio controls controlsList="nodownload"><source src="https://anonymous757575.github.io/diffariff-companion/audios/audio-cond/no-context/3/gen1.wav" type="audio/wav"> Your Browser does not support the audio tag </audio> </td>
    <td class="tg-0pky"> <audio controls controlsList="nodownload"><source src="https://anonymous757575.github.io/diffariff-companion/audios/audio-cond/no-context/3/gen2.wav" type="audio/wav"> Your Browser does not support the audio tag </audio> </td>
    <td class="tg-0pky"> <audio controls controlsList="nodownload"><source src="https://anonymous757575.github.io/diffariff-companion/audios/audio-cond/no-context/3/gen3.wav" type="audio/wav"> Your Browser does not support the audio tag </audio> </td>
  </tr>
</tbody>
</table>




### Bonus
In this section, we demonstrate additional controls derived from the use of a diffusion framework.

#### Inpainting
We can inpaint...
Tracks are inpainted from second 5 to 8.

<table class="tg">
<thead>
  <tr>
    <th class="tg-0pky">Context</th>
    <th class="tg-0lax">Masked Original Accompaniment</th>
    <!-- <th class="tg-0lax" colspan="4">Inpaintings</th> -->
    <th class="tg-0pky">Inpainting w/ Mix</th>
    <th class="tg-0lax">Inpainting Solo</th>
  </tr>
</thead>
<tbody>
  <tr>
    <td class="tg-0lax" rowspan="3"> <audio controls controlsList="nodownload"><source src="https://anonymous757575.github.io/diffariff-companion/audios/bonus/inpainting/1/context.wav" type="audio/wav"> Your Browser does not support the audio tag </audio> </td>
    <td class="tg-0lax" rowspan="3"> <audio controls controlsList="nodownload"><source src="https://anonymous757575.github.io/diffariff-companion/audios/bonus/inpainting/1/original_masked.wav" type="audio/wav"> Your Browser does not support the audio tag </audio> </td>
    <td class="tg-0lax"> <audio controls controlsList="nodownload"><source src="https://anonymous757575.github.io/diffariff-companion/audios/bonus/inpainting/1/inpainting0_mix.wav" type="audio/wav"> Your Browser does not support the audio tag </audio> </td>
    <td class="tg-0lax"> <audio controls controlsList="nodownload"><source src="https://anonymous757575.github.io/diffariff-companion/audios/bonus/inpainting/1/inpainting0.wav" type="audio/wav"> Your Browser does not support the audio tag </audio> </td>
  </tr>
  <tr>
    <td class="tg-0lax"> <audio controls controlsList="nodownload"><source src="https://anonymous757575.github.io/diffariff-companion/audios/bonus/inpainting/1/inpainting1_mix.wav" type="audio/wav"> Your Browser does not support the audio tag </audio> </td>
    <td class="tg-0lax"> <audio controls controlsList="nodownload"><source src="https://anonymous757575.github.io/diffariff-companion/audios/bonus/inpainting/1/inpainting1.wav" type="audio/wav"> Your Browser does not support the audio tag </audio> </td>
  </tr>
  <tr>
    <td class="tg-0lax"> <audio controls controlsList="nodownload"><source src="https://anonymous757575.github.io/diffariff-companion/audios/bonus/inpainting/1/inpainting2_mix.wav" type="audio/wav"> Your Browser does not support the audio tag </audio> </td>
    <td class="tg-0lax"> <audio controls controlsList="nodownload"><source src="https://anonymous757575.github.io/diffariff-companion/audios/bonus/inpainting/1/inpainting2.wav" type="audio/wav"> Your Browser does not support the audio tag </audio> </td>
  </tr>
<!-- new ctx -->
  <tr>
    <td class="tg-0lax" rowspan="3"> <audio controls controlsList="nodownload"><source src="https://anonymous757575.github.io/diffariff-companion/audios/bonus/inpainting/2/context.wav" type="audio/wav"> Your Browser does not support the audio tag </audio> </td>
    <td class="tg-0lax" rowspan="3"> <audio controls controlsList="nodownload"><source src="https://anonymous757575.github.io/diffariff-companion/audios/bonus/inpainting/2/original_masked.wav" type="audio/wav"> Your Browser does not support the audio tag </audio> </td>
    <td class="tg-0lax"> <audio controls controlsList="nodownload"><source src="https://anonymous757575.github.io/diffariff-companion/audios/bonus/inpainting/2/inpainting0_mix.wav" type="audio/wav"> Your Browser does not support the audio tag </audio> </td>
    <td class="tg-0lax"> <audio controls controlsList="nodownload"><source src="https://anonymous757575.github.io/diffariff-companion/audios/bonus/inpainting/2/inpainting0.wav" type="audio/wav"> Your Browser does not support the audio tag </audio> </td>
  </tr>
  <tr>
    <td class="tg-0lax"> <audio controls controlsList="nodownload"><source src="https://anonymous757575.github.io/diffariff-companion/audios/bonus/inpainting/2/inpainting1_mix.wav" type="audio/wav"> Your Browser does not support the audio tag </audio> </td>
    <td class="tg-0lax"> <audio controls controlsList="nodownload"><source src="https://anonymous757575.github.io/diffariff-companion/audios/bonus/inpainting/2/inpainting1.wav" type="audio/wav"> Your Browser does not support the audio tag </audio> </td>
  </tr>
  <tr>
    <td class="tg-0lax"> <audio controls controlsList="nodownload"><source src="https://anonymous757575.github.io/diffariff-companion/audios/bonus/inpainting/2/inpainting2_mix.wav" type="audio/wav"> Your Browser does not support the audio tag </audio> </td>
    <td class="tg-0lax"> <audio controls controlsList="nodownload"><source src="https://anonymous757575.github.io/diffariff-companion/audios/bonus/inpainting/2/inpainting2.wav" type="audio/wav"> Your Browser does not support the audio tag </audio> </td>
  </tr>
<!-- new ctx -->
  <tr>
    <td class="tg-0lax" rowspan="3"> <audio controls controlsList="nodownload"><source src="https://anonymous757575.github.io/diffariff-companion/audios/bonus/inpainting/3/context.wav" type="audio/wav"> Your Browser does not support the audio tag </audio> </td>
    <td class="tg-0lax" rowspan="3"> <audio controls controlsList="nodownload"><source src="https://anonymous757575.github.io/diffariff-companion/audios/bonus/inpainting/3/original_masked.wav" type="audio/wav"> Your Browser does not support the audio tag </audio> </td>
    <td class="tg-0lax"> <audio controls controlsList="nodownload"><source src="https://anonymous757575.github.io/diffariff-companion/audios/bonus/inpainting/3/inpainting0_mix.wav" type="audio/wav"> Your Browser does not support the audio tag </audio> </td>
    <td class="tg-0lax"> <audio controls controlsList="nodownload"><source src="https://anonymous757575.github.io/diffariff-companion/audios/bonus/inpainting/3/inpainting0.wav" type="audio/wav"> Your Browser does not support the audio tag </audio> </td>
  </tr>
  <tr>
    <td class="tg-0lax"> <audio controls controlsList="nodownload"><source src="https://anonymous757575.github.io/diffariff-companion/audios/bonus/inpainting/3/inpainting1_mix.wav" type="audio/wav"> Your Browser does not support the audio tag </audio> </td>
    <td class="tg-0lax"> <audio controls controlsList="nodownload"><source src="https://anonymous757575.github.io/diffariff-companion/audios/bonus/inpainting/3/inpainting1.wav" type="audio/wav"> Your Browser does not support the audio tag </audio> </td>
  </tr>
  <tr>
    <td class="tg-0lax"> <audio controls controlsList="nodownload"><source src="https://anonymous757575.github.io/diffariff-companion/audios/bonus/inpainting/3/inpainting2_mix.wav" type="audio/wav"> Your Browser does not support the audio tag </audio> </td>
    <td class="tg-0lax"> <audio controls controlsList="nodownload"><source src="https://anonymous757575.github.io/diffariff-companion/audios/bonus/inpainting/3/inpainting2.wav" type="audio/wav"> Your Browser does not support the audio tag </audio> </td>
  </tr>
<!-- new ctx -->
</tbody>
</table>

#### Interpolations
We can interpolate between different references in the CLAP space. Here, we demonstrate the impact of a interpolation between an audio-derived CLAP embedding and a text-derived one.

<table class="tg">
<tbody>
  <tr>
    <th class="tg-0pky"> Audio Reference </th>
    <td class="tg-0pky"> <audio controls controlsList="nodownload"><source src="https://anonymous757575.github.io/diffariff-companion/audios/bonus/interpolations/2/ref.wav" type="audio/wav"> Your Browser does not support the audio tag </audio> </td>
    <td class="tg-0pky"> <audio controls controlsList="nodownload"><source src="https://anonymous757575.github.io/diffariff-companion/audios/bonus/interpolations/3/ref.wav" type="audio/wav"> Your Browser does not support the audio tag </audio> </td>
    <td class="tg-0pky"> <audio controls controlsList="nodownload"><source src="https://anonymous757575.github.io/diffariff-companion/audios/bonus/interpolations/4/ref.wav" type="audio/wav"> Your Browser does not support the audio tag </audio> </td>
    <td class="tg-0pky"> <audio controls controlsList="nodownload"><source src="https://anonymous757575.github.io/diffariff-companion/audios/bonus/interpolations/5/ref.wav" type="audio/wav"> Your Browser does not support the audio tag </audio> </td>
  </tr>
  <tr>
    <th class="tg-0pky"> $$ t = 0 $$ </th>
    <td class="tg-0pky"> <audio controls controlsList="nodownload"><source src="https://anonymous757575.github.io/diffariff-companion/audios/bonus/interpolations/2/gen0.wav" type="audio/wav"> Your Browser does not support the audio tag </audio> </td>
    <td class="tg-0pky"> <audio controls controlsList="nodownload"><source src="https://anonymous757575.github.io/diffariff-companion/audios/bonus/interpolations/3/gen0.wav" type="audio/wav"> Your Browser does not support the audio tag </audio> </td>
    <td class="tg-0pky"> <audio controls controlsList="nodownload"><source src="https://anonymous757575.github.io/diffariff-companion/audios/bonus/interpolations/4/gen0.wav" type="audio/wav"> Your Browser does not support the audio tag </audio> </td>
    <td class="tg-0pky"> <audio controls controlsList="nodownload"><source src="https://anonymous757575.github.io/diffariff-companion/audios/bonus/interpolations/5/gen0.wav" type="audio/wav"> Your Browser does not support the audio tag </audio> </td>
  </tr>
  <tr>
    <th class="tg-0pky"> $$ t = 0.2 $$ </th>
    <td class="tg-0pky"> <audio controls controlsList="nodownload"><source src="https://anonymous757575.github.io/diffariff-companion/audios/bonus/interpolations/2/gen0.2.wav" type="audio/wav"> Your Browser does not support the audio tag </audio> </td>
    <td class="tg-0pky"> <audio controls controlsList="nodownload"><source src="https://anonymous757575.github.io/diffariff-companion/audios/bonus/interpolations/3/gen0.2.wav" type="audio/wav"> Your Browser does not support the audio tag </audio> </td>
    <td class="tg-0pky"> <audio controls controlsList="nodownload"><source src="https://anonymous757575.github.io/diffariff-companion/audios/bonus/interpolations/4/gen0.2.wav" type="audio/wav"> Your Browser does not support the audio tag </audio> </td>
    <td class="tg-0pky"> <audio controls controlsList="nodownload"><source src="https://anonymous757575.github.io/diffariff-companion/audios/bonus/interpolations/5/gen0.2.wav" type="audio/wav"> Your Browser does not support the audio tag </audio> </td>
  </tr>

  <tr>
    <th class="tg-0pky"> $$ t = 0.4 $$ </th>
    <td class="tg-0pky"> <audio controls controlsList="nodownload"><source src="https://anonymous757575.github.io/diffariff-companion/audios/bonus/interpolations/2/gen0.4.wav" type="audio/wav"> Your Browser does not support the audio tag </audio> </td>
    <td class="tg-0pky"> <audio controls controlsList="nodownload"><source src="https://anonymous757575.github.io/diffariff-companion/audios/bonus/interpolations/3/gen0.4.wav" type="audio/wav"> Your Browser does not support the audio tag </audio> </td>
    <td class="tg-0pky"> <audio controls controlsList="nodownload"><source src="https://anonymous757575.github.io/diffariff-companion/audios/bonus/interpolations/4/gen0.4.wav" type="audio/wav"> Your Browser does not support the audio tag </audio> </td>
    <td class="tg-0pky"> <audio controls controlsList="nodownload"><source src="https://anonymous757575.github.io/diffariff-companion/audios/bonus/interpolations/5/gen0.4.wav" type="audio/wav"> Your Browser does not support the audio tag </audio> </td>
  </tr>
  <tr>
    <th class="tg-0pky"> $$ t = 0.6 $$ </th>
    <td class="tg-0pky"> <audio controls controlsList="nodownload"><source src="https://anonymous757575.github.io/diffariff-companion/audios/bonus/interpolations/2/gen0.6.wav" type="audio/wav"> Your Browser does not support the audio tag </audio> </td>
    <td class="tg-0pky"> <audio controls controlsList="nodownload"><source src="https://anonymous757575.github.io/diffariff-companion/audios/bonus/interpolations/3/gen0.6.wav" type="audio/wav"> Your Browser does not support the audio tag </audio> </td>
    <td class="tg-0pky"> <audio controls controlsList="nodownload"><source src="https://anonymous757575.github.io/diffariff-companion/audios/bonus/interpolations/4/gen0.6.wav" type="audio/wav"> Your Browser does not support the audio tag </audio> </td>
    <td class="tg-0pky"> <audio controls controlsList="nodownload"><source src="https://anonymous757575.github.io/diffariff-companion/audios/bonus/interpolations/5/gen0.6.wav" type="audio/wav"> Your Browser does not support the audio tag </audio> </td>
  </tr>
  <tr>
    <th class="tg-0pky"> $$ t = 0.8 $$ </th>
    <td class="tg-0pky"> <audio controls controlsList="nodownload"><source src="https://anonymous757575.github.io/diffariff-companion/audios/bonus/interpolations/2/gen0.8.wav" type="audio/wav"> Your Browser does not support the audio tag </audio> </td>
    <td class="tg-0pky"> <audio controls controlsList="nodownload"><source src="https://anonymous757575.github.io/diffariff-companion/audios/bonus/interpolations/3/gen0.8.wav" type="audio/wav"> Your Browser does not support the audio tag </audio> </td>
    <td class="tg-0pky"> <audio controls controlsList="nodownload"><source src="https://anonymous757575.github.io/diffariff-companion/audios/bonus/interpolations/4/gen0.8.wav" type="audio/wav"> Your Browser does not support the audio tag </audio> </td>
    <td class="tg-0pky"> <audio controls controlsList="nodownload"><source src="https://anonymous757575.github.io/diffariff-companion/audios/bonus/interpolations/5/gen0.8.wav" type="audio/wav"> Your Browser does not support the audio tag </audio> </td>
  </tr>
  <tr>
    <th class="tg-0pky"> $$ t = 1 $$ </th>
    <td class="tg-0pky"> <audio controls controlsList="nodownload"><source src="https://anonymous757575.github.io/diffariff-companion/audios/bonus/interpolations/2/gen1.wav" type="audio/wav"> Your Browser does not support the audio tag </audio> </td>
    <td class="tg-0pky"> <audio controls controlsList="nodownload"><source src="https://anonymous757575.github.io/diffariff-companion/audios/bonus/interpolations/3/gen1.wav" type="audio/wav"> Your Browser does not support the audio tag </audio> </td>
    <td class="tg-0pky"> <audio controls controlsList="nodownload"><source src="https://anonymous757575.github.io/diffariff-companion/audios/bonus/interpolations/4/gen1.wav" type="audio/wav"> Your Browser does not support the audio tag </audio> </td>
    <td class="tg-0pky"> <audio controls controlsList="nodownload"><source src="https://anonymous757575.github.io/diffariff-companion/audios/bonus/interpolations/5/gen1.wav" type="audio/wav"> Your Browser does not support the audio tag </audio> </td>
  </tr>
    <tr>
    <th class="tg-0pky"> Text Prompt </th>
    <td class="tg-0pky"> "Latin Percussion" </td>
    <td class="tg-0pky"> "Oriental Percussion Texture" </td>
    <td class="tg-0pky"> "The Cathciest Darbouka Rhythm" </td>
    <td class="tg-0pky"> "Rhythm on Huge Industrial Metal Plates" </td>
  </tr>
  
</tbody>
</table>

#### Variations
Given an audio file, we can encode it in the CAE latent space and get the corresponding latent sequence. By adding very little noise to it, and denoising this noisy sequence again, we end up with a variation of the first sequence. We can then decode it to obtain a variation of the input audio.

<table class="tg">
<thead>
  <tr>
    <th class="tg-0pky">Reference</th>
    <th class="tg-0lax">Variation strength = 0.2</th>
    <th class="tg-0lax">0.5</th>
    <th class="tg-0lax">0.8</th>

  </tr>
</thead>
<tbody>
  <tr>
    <td class="tg-0lax"> <audio controls controlsList="nodownload"><source src="https://anonymous757575.github.io/diffariff-companion/audios/bonus/variations/1/orig.wav" type="audio/wav"> Your Browser does not support the audio tag </audio> </td>
    <td class="tg-0lax"> <audio controls controlsList="nodownload"><source src="https://anonymous757575.github.io/diffariff-companion/audios/bonus/variations/1/0.20.wav" type="audio/wav"> Your Browser does not support the audio tag </audio> </td>
    <td class="tg-0lax"> <audio controls controlsList="nodownload"><source src="https://anonymous757575.github.io/diffariff-companion/audios/bonus/variations/1/0.50.wav" type="audio/wav"> Your Browser does not support the audio tag </audio> </td>
    <td class="tg-0lax"> <audio controls controlsList="nodownload"><source src="https://anonymous757575.github.io/diffariff-companion/audios/bonus/variations/1/0.80.wav" type="audio/wav"> Your Browser does not support the audio tag </audio> </td>
  </tr>
  <tr>
    <td class="tg-0lax"> <audio controls controlsList="nodownload"><source src="https://anonymous757575.github.io/diffariff-companion/audios/bonus/variations/2/orig.wav" type="audio/wav"> Your Browser does not support the audio tag </audio> </td>
    <td class="tg-0lax"> <audio controls controlsList="nodownload"><source src="https://anonymous757575.github.io/diffariff-companion/audios/bonus/variations/2/0.20.wav" type="audio/wav"> Your Browser does not support the audio tag </audio> </td>
    <td class="tg-0lax"> <audio controls controlsList="nodownload"><source src="https://anonymous757575.github.io/diffariff-companion/audios/bonus/variations/2/0.50.wav" type="audio/wav"> Your Browser does not support the audio tag </audio> </td>
    <td class="tg-0lax"> <audio controls controlsList="nodownload"><source src="https://anonymous757575.github.io/diffariff-companion/audios/bonus/variations/2/0.80.wav" type="audio/wav"> Your Browser does not support the audio tag </audio> </td>
  </tr>
  <tr>
    <td class="tg-0lax"> <audio controls controlsList="nodownload"><source src="https://anonymous757575.github.io/diffariff-companion/audios/bonus/variations/3/orig.wav" type="audio/wav"> Your Browser does not support the audio tag </audio> </td>
    <td class="tg-0lax"> <audio controls controlsList="nodownload"><source src="https://anonymous757575.github.io/diffariff-companion/audios/bonus/variations/3/0.20.wav" type="audio/wav"> Your Browser does not support the audio tag </audio> </td>
    <td class="tg-0lax"> <audio controls controlsList="nodownload"><source src="https://anonymous757575.github.io/diffariff-companion/audios/bonus/variations/3/0.50.wav" type="audio/wav"> Your Browser does not support the audio tag </audio> </td>
    <td class="tg-0lax"> <audio controls controlsList="nodownload"><source src="https://anonymous757575.github.io/diffariff-companion/audios/bonus/variations/3/0.80.wav" type="audio/wav"> Your Browser does not support the audio tag </audio> </td>
  </tr>
  <tr>
    <td class="tg-0lax"> <audio controls controlsList="nodownload"><source src="https://anonymous757575.github.io/diffariff-companion/audios/bonus/variations/4/orig.wav" type="audio/wav"> Your Browser does not support the audio tag </audio> </td>
    <td class="tg-0lax"> <audio controls controlsList="nodownload"><source src="https://anonymous757575.github.io/diffariff-companion/audios/bonus/variations/4/0.20.wav" type="audio/wav"> Your Browser does not support the audio tag </audio> </td>
    <td class="tg-0lax"> <audio controls controlsList="nodownload"><source src="https://anonymous757575.github.io/diffariff-companion/audios/bonus/variations/4/0.50.wav" type="audio/wav"> Your Browser does not support the audio tag </audio> </td>
    <td class="tg-0lax"> <audio controls controlsList="nodownload"><source src="https://anonymous757575.github.io/diffariff-companion/audios/bonus/variations/4/0.80.wav" type="audio/wav"> Your Browser does not support the audio tag </audio> </td>
  </tr>

</tbody>
</table>

#### Stereo width
Based on the exact same principle as the one used for variations, for any mono signal, we can create a tiny variation of it and use the original and the variation as left and right channels, creating what we call pseudo-stereo. Here, you can find examples of pseudo stereo files, generated from different stereo width ratios.

<table class="tg">
<thead>
  <tr>
    <th class="tg-0pky">Stereo Width = 0</th>
    <th class="tg-0lax">0.2</th>
    <th class="tg-0lax">0.4</th>
    <th class="tg-0lax">0.5</th>

  </tr>
</thead>
<tbody>
  <tr>
    <td class="tg-0lax"> <audio controls controlsList="nodownload"><source src="https://anonymous757575.github.io/diffariff-companion/audios/bonus/stereo/1/0.0.wav" type="audio/wav"> Your Browser does not support the audio tag </audio> </td>
    <td class="tg-0lax"> <audio controls controlsList="nodownload"><source src="https://anonymous757575.github.io/diffariff-companion/audios/bonus/stereo/1/0.2.wav" type="audio/wav"> Your Browser does not support the audio tag </audio> </td>
    <td class="tg-0lax"> <audio controls controlsList="nodownload"><source src="https://anonymous757575.github.io/diffariff-companion/audios/bonus/stereo/1/0.4.wav" type="audio/wav"> Your Browser does not support the audio tag </audio> </td>
    <td class="tg-0lax"> <audio controls controlsList="nodownload"><source src="https://anonymous757575.github.io/diffariff-companion/audios/bonus/stereo/1/0.5.wav" type="audio/wav"> Your Browser does not support the audio tag </audio> </td>
  </tr>
  <tr>
    <td class="tg-0lax"> <audio controls controlsList="nodownload"><source src="https://anonymous757575.github.io/diffariff-companion/audios/bonus/stereo/2/0.0.wav" type="audio/wav"> Your Browser does not support the audio tag </audio> </td>
    <td class="tg-0lax"> <audio controls controlsList="nodownload"><source src="https://anonymous757575.github.io/diffariff-companion/audios/bonus/stereo/2/0.2.wav" type="audio/wav"> Your Browser does not support the audio tag </audio> </td>
    <td class="tg-0lax"> <audio controls controlsList="nodownload"><source src="https://anonymous757575.github.io/diffariff-companion/audios/bonus/stereo/2/0.4.wav" type="audio/wav"> Your Browser does not support the audio tag </audio> </td>
    <td class="tg-0lax"> <audio controls controlsList="nodownload"><source src="https://anonymous757575.github.io/diffariff-companion/audios/bonus/stereo/2/0.5.wav" type="audio/wav"> Your Browser does not support the audio tag </audio> </td>
  </tr>
    <tr>
    <td class="tg-0lax"> <audio controls controlsList="nodownload"><source src="https://anonymous757575.github.io/diffariff-companion/audios/bonus/stereo/3/0.0.wav" type="audio/wav"> Your Browser does not support the audio tag </audio> </td>
    <td class="tg-0lax"> <audio controls controlsList="nodownload"><source src="https://anonymous757575.github.io/diffariff-companion/audios/bonus/stereo/3/0.2.wav" type="audio/wav"> Your Browser does not support the audio tag </audio> </td>
    <td class="tg-0lax"> <audio controls controlsList="nodownload"><source src="https://anonymous757575.github.io/diffariff-companion/audios/bonus/stereo/3/0.4.wav" type="audio/wav"> Your Browser does not support the audio tag </audio> </td>
    <td class="tg-0lax"> <audio controls controlsList="nodownload"><source src="https://anonymous757575.github.io/diffariff-companion/audios/bonus/stereo/3/0.5.wav" type="audio/wav"> Your Browser does not support the audio tag </audio> </td>
  </tr>
</tbody>
</table>

#### Loop Sampling
Loop ?

<table class="tg">
<thead>
  <tr>
    <th class="tg-0pky">Number of Repetitions</th>
    <th class="tg-0pky">Loop Strength</th>
    <th class="tg-0lax" colspan="3">Generations</th>
  </tr>
</thead>
<tbody>
  <tr>
    <td class="tg-0pky" rowspan="3"> 2 </td>
    <td class="tg-0pky">0.5</td>
    <td class="tg-0lax"> <audio controls controlsList="nodownload"><source src="https://anonymous757575.github.io/diffariff-companion/audios/bonus/loops/0.5_2_reps.wav"> Your Browser does not support the audio tag </audio> </td>
    <td class="tg-0lax"> <audio controls controlsList="nodownload"><source src="https://anonymous757575.github.io/diffariff-companion/audios/bonus/loops/0.5_2_reps_1.wav"> Your Browser does not support the audio tag </audio> </td>
    <td class="tg-0lax"> <audio controls controlsList="nodownload"><source src="https://anonymous757575.github.io/diffariff-companion/audios/bonus/loops/0.5_2_reps_2.wav"> Your Browser does not support the audio tag </audio> </td>
  </tr>
  <tr>
    <td class="tg-0pky">0.8</td>
    <td class="tg-0lax"> <audio controls controlsList="nodownload"><source src="https://anonymous757575.github.io/diffariff-companion/audios/bonus/loops/0.8_2_reps.wav"> Your Browser does not support the audio tag </audio> </td>
    <td class="tg-0lax"> <audio controls controlsList="nodownload"><source src="https://anonymous757575.github.io/diffariff-companion/audios/bonus/loops/0.8_2_reps_1.wav"> Your Browser does not support the audio tag </audio> </td>
    <td class="tg-0lax"> <audio controls controlsList="nodownload"><source src="https://anonymous757575.github.io/diffariff-companion/audios/bonus/loops/0.8_2_reps_2.wav"> Your Browser does not support the audio tag </audio> </td>
  </tr>
  <tr>
    <td class="tg-0pky">1</td>
    <td class="tg-0lax"> <audio controls controlsList="nodownload"><source src="https://anonymous757575.github.io/diffariff-companion/audios/bonus/loops/1_2_reps.wav"> Your Browser does not support the audio tag </audio> </td>
    <td class="tg-0lax"> <audio controls controlsList="nodownload"><source src="https://anonymous757575.github.io/diffariff-companion/audios/bonus/loops/1_2_reps_1.wav"> Your Browser does not support the audio tag </audio> </td>
    <td class="tg-0lax"> <audio controls controlsList="nodownload"><source src="https://anonymous757575.github.io/diffariff-companion/audios/bonus/loops/1_2_reps_2.wav"> Your Browser does not support the audio tag </audio> </td>
  </tr>
  <tr>
    <td class="tg-0pky" rowspan="3"> 4 </td>
    <td class="tg-0pky">0.5</td>
    <td class="tg-0lax"> <audio controls controlsList="nodownload"><source src="https://anonymous757575.github.io/diffariff-companion/audios/bonus/loops/0.5_4_reps.wav"> Your Browser does not support the audio tag </audio> </td>
    <td class="tg-0lax"> <audio controls controlsList="nodownload"><source src="https://anonymous757575.github.io/diffariff-companion/audios/bonus/loops/0.5_4_reps_1.wav"> Your Browser does not support the audio tag </audio> </td>
    <td class="tg-0lax"> <audio controls controlsList="nodownload"><source src="https://anonymous757575.github.io/diffariff-companion/audios/bonus/loops/0.5_4_reps_2.wav"> Your Browser does not support the audio tag </audio> </td>
  </tr>
  <tr>
    <td class="tg-0pky">0.8</td>
    <td class="tg-0lax"> <audio controls controlsList="nodownload"><source src="https://anonymous757575.github.io/diffariff-companion/audios/bonus/loops/0.8_4_reps.wav"> Your Browser does not support the audio tag </audio> </td>
    <td class="tg-0lax"> <audio controls controlsList="nodownload"><source src="https://anonymous757575.github.io/diffariff-companion/audios/bonus/loops/0.8_4_reps_1.wav"> Your Browser does not support the audio tag </audio> </td>
    <td class="tg-0lax"> <audio controls controlsList="nodownload"><source src="https://anonymous757575.github.io/diffariff-companion/audios/bonus/loops/0.8_4_reps_2.wav"> Your Browser does not support the audio tag </audio> </td>
  </tr>
  <tr>
    <td class="tg-0pky">1</td>
    <td class="tg-0lax"> <audio controls controlsList="nodownload"><source src="https://anonymous757575.github.io/diffariff-companion/audios/bonus/loops/1_4_reps.wav"> Your Browser does not support the audio tag </audio> </td>
    <td class="tg-0lax"> <audio controls controlsList="nodownload"><source src="https://anonymous757575.github.io/diffariff-companion/audios/bonus/loops/1_4_reps_1.wav"> Your Browser does not support the audio tag </audio> </td>
    <td class="tg-0lax"> <audio controls controlsList="nodownload"><source src="https://anonymous757575.github.io/diffariff-companion/audios/bonus/loops/1_4_reps_2.wav"> Your Browser does not support the audio tag </audio> </td>
  </tr>
</tbody>
</table>


## User Study Sample Questions
Here, you can find examples of the questions participants had to answer in our user studies. The user studies were conducted using the [GoListen](https://golisten.ucd.ie/) online platform [[1](#references)]. Citation will be added in the camera-ready version.

### Audio Quality Assessment 

[Here is a link to a demo of the Quality Assessment test.](https://golisten.ucd.ie/task/acr-test/662643b2552c347eae00849d)

### Subjective Audio Prompt Adherence

[Here is a link to a demo of the Subjective Audio Prompt Adherence test.](https://golisten.ucd.ie/task/mushra-test/662644d5552c347eae00849e)

## References
[1] *Barry, Dan, et al. "Go Listen: An End-to-End Online Listening Test Platform." Journal of Open Research Software 9.1 (2021)*