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

**This website is a work in progress that will be completed by April 23rd.**

This is the accompanying website to "Diff-a-Riff: Musical Accompaniment Co-creation via Latent Diffusion Models" submitted to ISMIR 2024.

* [System's Overview](#systems-overview)
* [Sound Examples](#sound-examples)
  + [Context-based Control](#context-based-control)
  + [Text-based Control](#text-based-control)
    - [With Context](#with-context)
    - [Without context](#without-context)
  + [Audio-based Control](#audio-based-control)
    - [With Context](#with-context-1)
    - [Without Context](#without-context)
    - [Complete Music Excerpts](#complete-music-excerpts)
  + [Fully Unconditional](#fully-unconditional)
  + [Bonus](#bonus)
    - [Inpainting](#inpainting)
    - [Interpolations](#interpolations)
    - [Variations](#variations)
    - [Loop Sampling](#loop-sampling)
    - [Stereo width](#stereo-width)
* [User Study Sample Questions](#user-study-sample-questions)
  + [Audio Quality Assessment](#audio-quality-assessment)
  + [Subjective Audio Prompt Adherence](#subjective-audio-prompt-adherence)
* [References](#references)

## System's Overview 
<!-- ![Overview of Diff-A-Riff](https://anonymous757575.github.io/diffariff-companion/diff-a-riff-website.png "Title") -->

<figure>
  <img src="https://anonymous757575.github.io/diffariff-companion/diff-a-riff-website.png" alt="Overview of Diff-A-Riff"/>
  <figcaption>Overview of Diff-A-Riff. The CAE Encoder transforms the music context into a compressed representation, concatenated with a noisy sample, and further processed through the multi-scale U-Net. The generated latent sequence is decoded into audio via the CAE Decoder. We highlight frozen components in blue and trainable elements in orange. At inference time, the conditioning signals are optional and one can try different conditional setups.</figcaption>
</figure>


## Sound Examples
In this section, we demonstrate the generation abilities of our model under different conditioning signals.

### Context-based Control
Given an existing piece of music, Diff-A-Riff allows the generation of various accompaniments. Here, we present various context music pieces and accompaniments generated conditioned on this context only.

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



### Text-based Control


#### With Context
Given a context music piece, Diff-A-Riff allows the generation of accompaniments based on a text prompt. Here, we present various context music pieces and various text-based accompaniments.


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
    <td class="tg-0lax"> <audio controls controlsList="nodownload"><source src="https://anonymous757575.github.io/diffariff-companion/audios/text-cond/context/1/prompt1/gen1_mix.wav"> Your Browser does not support the audio tag </audio> </td>
    <td class="tg-0lax"> <audio controls controlsList="nodownload"><source src="https://anonymous757575.github.io/diffariff-companion/audios/text-cond/context/1/prompt1/gen2_mix.wav"> Your Browser does not support the audio tag </audio> </td>
  </tr>
  <tr>
    <td class="tg-0pky">"A mellow synthesizer playing ethereal pads."</td>
    <td class="tg-0lax"> <audio controls controlsList="nodownload"><source src="https://anonymous757575.github.io/diffariff-companion/audios/text-cond/context/1/prompt2/gen1_mix.wav" type="audio/wav"> Your Browser does not support the audio tag </audio> </td>
    <td class="tg-0pky"> <audio controls controlsList="nodownload"><source src="https://anonymous757575.github.io/diffariff-companion/audios/text-cond/context/1/prompt2/gen2_mix.wav" type="audio/wav"> Your Browser does not support the audio tag </audio> </td>
  </tr>
  <tr>
    <td class="tg-0pky" rowspan="2"> <audio controls controlsList="nodownload"><source src="https://anonymous757575.github.io/diffariff-companion/audios/text-cond/context/2/context.mp3" type="audio/wav"> Your Browser does not support the audio tag </audio> </td>
    <td class="tg-0pky">"Drums with reverb and a lot of toms."</td>
    <td class="tg-0lax"> <audio controls controlsList="nodownload"><source src="https://anonymous757575.github.io/diffariff-companion/audios/text-cond/context/2/prompt1/gen1_mix.wav"> Your Browser does not support the audio tag </audio> </td>
    <td class="tg-0lax"> <audio controls controlsList="nodownload"><source src="https://anonymous757575.github.io/diffariff-companion/audios/text-cond/context/2/prompt1/gen2_mix.wav"> Your Browser does not support the audio tag </audio> </td>
  </tr>
  <tr>
    <td class="tg-0pky">"Drums with reverb and a lot of soft hats."</td>
    <td class="tg-0lax"> <audio controls controlsList="nodownload"><source src="https://anonymous757575.github.io/diffariff-companion/audios/text-cond/context/2/prompt2/gen1_mix.wav" type="audio/wav"> Your Browser does not support the audio tag </audio> </td>
    <td class="tg-0pky"> <audio controls controlsList="nodownload"><source src="https://anonymous757575.github.io/diffariff-companion/audios/text-cond/context/2/prompt2/gen2_mix.wav" type="audio/wav"> Your Browser does not support the audio tag </audio> </td>
  </tr>
</tbody>
</table>

#### Without context 
Diff-A-Riff also allows the generation of solo instrument tracks conditioned on text only.


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
</tbody>
</table>


### Audio-based Control

#### With Context
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


#### Without Context 
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

#### Complete Music Excerpts

Here you can find excerpts of multitrack music
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

### Fully Unconditional
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
  
</tbody>
</table>

### Bonus
In this section, we demonstrate controls derived from the use of a diffusion framework.

#### Inpainting

#### Interpolations

#### Variations

#### Loop Sampling

#### Stereo width

<table class="tg">
<thead>
  <tr>
    <th class="tg-0pky">Stereo Width = 0</th>
    <th class="tg-0lax">0.1</th>
    <th class="tg-0lax">0.2</th>
    <th class="tg-0lax">0.3</th>
    <th class="tg-0lax">0.4</th>
    <th class="tg-0lax">0.5</th>

  </tr>
</thead>
<tbody>
  <tr>
    <td class="tg-0lax"> <audio controls controlsList="nodownload"><source src="https://anonymous757575.github.io/diffariff-companion/audios/bonus/stereo/1/0.0.wav" type="audio/wav"> Your Browser does not support the audio tag </audio> </td>
    <td class="tg-0lax"> <audio controls controlsList="nodownload"><source src="https://anonymous757575.github.io/diffariff-companion/audios/bonus/stereo/1/0.1.wav" type="audio/wav"> Your Browser does not support the audio tag </audio> </td>
    <td class="tg-0lax"> <audio controls controlsList="nodownload"><source src="https://anonymous757575.github.io/diffariff-companion/audios/bonus/stereo/1/0.2.wav" type="audio/wav"> Your Browser does not support the audio tag </audio> </td>
    <td class="tg-0lax"> <audio controls controlsList="nodownload"><source src="https://anonymous757575.github.io/diffariff-companion/audios/bonus/stereo/1/0.3.wav" type="audio/wav"> Your Browser does not support the audio tag </audio> </td>
    <td class="tg-0lax"> <audio controls controlsList="nodownload"><source src="https://anonymous757575.github.io/diffariff-companion/audios/bonus/stereo/1/0.4.wav" type="audio/wav"> Your Browser does not support the audio tag </audio> </td>
    <td class="tg-0lax"> <audio controls controlsList="nodownload"><source src="https://anonymous757575.github.io/diffariff-companion/audios/bonus/stereo/1/0.5.wav" type="audio/wav"> Your Browser does not support the audio tag </audio> </td>
  </tr>
  <tr>
    <td class="tg-0lax"> <audio controls controlsList="nodownload"><source src="https://anonymous757575.github.io/diffariff-companion/audios/bonus/stereo/2/0.0.wav" type="audio/wav"> Your Browser does not support the audio tag </audio> </td>
    <td class="tg-0lax"> <audio controls controlsList="nodownload"><source src="https://anonymous757575.github.io/diffariff-companion/audios/bonus/stereo/2/0.1.wav" type="audio/wav"> Your Browser does not support the audio tag </audio> </td>
    <td class="tg-0lax"> <audio controls controlsList="nodownload"><source src="https://anonymous757575.github.io/diffariff-companion/audios/bonus/stereo/2/0.2.wav" type="audio/wav"> Your Browser does not support the audio tag </audio> </td>
    <td class="tg-0lax"> <audio controls controlsList="nodownload"><source src="https://anonymous757575.github.io/diffariff-companion/audios/bonus/stereo/2/0.3.wav" type="audio/wav"> Your Browser does not support the audio tag </audio> </td>
    <td class="tg-0lax"> <audio controls controlsList="nodownload"><source src="https://anonymous757575.github.io/diffariff-companion/audios/bonus/stereo/2/0.4.wav" type="audio/wav"> Your Browser does not support the audio tag </audio> </td>
    <td class="tg-0lax"> <audio controls controlsList="nodownload"><source src="https://anonymous757575.github.io/diffariff-companion/audios/bonus/stereo/2/0.5.wav" type="audio/wav"> Your Browser does not support the audio tag </audio> </td>
  </tr>
    <tr>
    <td class="tg-0lax"> <audio controls controlsList="nodownload"><source src="https://anonymous757575.github.io/diffariff-companion/audios/bonus/stereo/3/0.0.wav" type="audio/wav"> Your Browser does not support the audio tag </audio> </td>
    <td class="tg-0lax"> <audio controls controlsList="nodownload"><source src="https://anonymous757575.github.io/diffariff-companion/audios/bonus/stereo/3/0.1.wav" type="audio/wav"> Your Browser does not support the audio tag </audio> </td>
    <td class="tg-0lax"> <audio controls controlsList="nodownload"><source src="https://anonymous757575.github.io/diffariff-companion/audios/bonus/stereo/3/0.2.wav" type="audio/wav"> Your Browser does not support the audio tag </audio> </td>
    <td class="tg-0lax"> <audio controls controlsList="nodownload"><source src="https://anonymous757575.github.io/diffariff-companion/audios/bonus/stereo/3/0.3.wav" type="audio/wav"> Your Browser does not support the audio tag </audio> </td>
    <td class="tg-0lax"> <audio controls controlsList="nodownload"><source src="https://anonymous757575.github.io/diffariff-companion/audios/bonus/stereo/3/0.4.wav" type="audio/wav"> Your Browser does not support the audio tag </audio> </td>
    <td class="tg-0lax"> <audio controls controlsList="nodownload"><source src="https://anonymous757575.github.io/diffariff-companion/audios/bonus/stereo/3/0.5.wav" type="audio/wav"> Your Browser does not support the audio tag </audio> </td>
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