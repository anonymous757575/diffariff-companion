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

**This website is a work in progress that will be completed by April 17th.**

This is the accompanying website to "Diff-a-Riff: Musical Accompaniment Co-creation via Latent Diffusion Models" submitted to ISMIR 2024.

* [Sound Examples](#sound-examples)
  + [Context-based Control](#context-based-control)
  + [Text-based Control](#text-based-control)
    - [With Context](#with-context)
    - [Without context](#without-context)
  + [Audio-based Control](#audio-based-control)
    - [With Context](#with-context-1)
    - [Without Context](#without-context)
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
    <td class="tg-0pky"> <audio controls controlsList="nodownload"><source src="https://anonymous757575.github.io/diffariff-companion/audios/sample.wav" type="audio/wav"> Your Browser does not support the audio tag </audio> </td>
    <td class="tg-0pky"> <audio controls controlsList="nodownload"><source src="https://anonymous757575.github.io/diffariff-companion/audios/sample.wav" type="audio/wav"> Your Browser does not support the audio tag </audio> </td>
    <td class="tg-0pky"> <audio controls controlsList="nodownload"><source src="https://anonymous757575.github.io/diffariff-companion/audios/sample.wav" type="audio/wav"> Your Browser does not support the audio tag </audio> </td>
    <td class="tg-0pky"> <audio controls controlsList="nodownload"><source src="https://anonymous757575.github.io/diffariff-companion/audios/sample.wav" type="audio/wav"> Your Browser does not support the audio tag </audio> </td>
    <td class="tg-0pky"> <audio controls controlsList="nodownload"><source src="https://anonymous757575.github.io/diffariff-companion/audios/sample.wav" type="audio/wav"> Your Browser does not support the audio tag </audio></td>
  </tr>
  <tr>
    <td class="tg-0pky"> <audio controls controlsList="nodownload"><source src="https://anonymous757575.github.io/diffariff-companion/audios/sample.wav" type="audio/wav"> Your Browser does not support the audio tag </audio> </td>
    <td class="tg-0pky"> <audio controls controlsList="nodownload"><source src="https://anonymous757575.github.io/diffariff-companion/audios/sample.wav" type="audio/wav"> Your Browser does not support the audio tag </audio> </td>
    <td class="tg-0pky"> <audio controls controlsList="nodownload"><source src="https://anonymous757575.github.io/diffariff-companion/audios/sample.wav" type="audio/wav"> Your Browser does not support the audio tag </audio> </td>
    <td class="tg-0pky"> <audio controls controlsList="nodownload"><source src="https://anonymous757575.github.io/diffariff-companion/audios/sample.wav" type="audio/wav"> Your Browser does not support the audio tag </audio> </td>
    <td class="tg-0pky"> <audio controls controlsList="nodownload"><source src="https://anonymous757575.github.io/diffariff-companion/audios/sample.wav" type="audio/wav"> Your Browser does not support the audio tag </audio> </td>
  </tr>
  <tr>
    <td class="tg-0pky"> <audio controls controlsList="nodownload"><source src="https://anonymous757575.github.io/diffariff-companion/audios/sample.wav" type="audio/wav"> Your Browser does not support the audio tag </audio> </td>
    <td class="tg-0pky"> <audio controls controlsList="nodownload"><source src="https://anonymous757575.github.io/diffariff-companion/audios/sample.wav" type="audio/wav"> Your Browser does not support the audio tag </audio> </td>
    <td class="tg-0pky"> <audio controls controlsList="nodownload"><source src="https://anonymous757575.github.io/diffariff-companion/audios/sample.wav" type="audio/wav"> Your Browser does not support the audio tag </audio> </td>
    <td class="tg-0pky"> <audio controls controlsList="nodownload"><source src="https://anonymous757575.github.io/diffariff-companion/audios/sample.wav" type="audio/wav"> Your Browser does not support the audio tag </audio> </td>
    <td class="tg-0pky"> <audio controls controlsList="nodownload"><source src="https://anonymous757575.github.io/diffariff-companion/audios/sample.wav" type="audio/wav"> Your Browser does not support the audio tag </audio> </td>
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
    <td class="tg-0pky" rowspan="2"> <audio controls controlsList="nodownload"><source src="https://anonymous757575.github.io/diffariff-companion/audios/sample.wav" type="audio/wav"> Your Browser does not support the audio tag </audio> </td>
    <td class="tg-0pky">"Example Prompt"</td>
    <td class="tg-0lax"> <audio controls controlsList="nodownload"><source src="https://anonymous757575.github.io/diffariff-companion/audios/sample.wav" type="audio/wav"> Your Browser does not support the audio tag </audio> </td>
    <td class="tg-0pky"> <audio controls controlsList="nodownload"><source src="https://anonymous757575.github.io/diffariff-companion/audios/sample.wav" type="audio/wav"> Your Browser does not support the audio tag </audio> </td>
    <td class="tg-0pky"> <audio controls controlsList="nodownload"><source src="https://anonymous757575.github.io/diffariff-companion/audios/sample.wav" type="audio/wav"> Your Browser does not support the audio tag </audio> </td>
  </tr>
  <tr>
    <td class="tg-0pky">"Example Prompt"</td>
    <td class="tg-0lax"> <audio controls controlsList="nodownload"><source src="https://anonymous757575.github.io/diffariff-companion/audios/sample.wav" type="audio/wav"> Your Browser does not support the audio tag </audio> </td>
    <td class="tg-0pky"> <audio controls controlsList="nodownload"><source src="https://anonymous757575.github.io/diffariff-companion/audios/sample.wav" type="audio/wav"> Your Browser does not support the audio tag </audio> </td>
    <td class="tg-0pky"> <audio controls controlsList="nodownload"><source src="https://anonymous757575.github.io/diffariff-companion/audios/sample.wav" type="audio/wav"> Your Browser does not support the audio tag </audio> </td>
  </tr>
  <tr>
    <td class="tg-0pky" rowspan="2"> <audio controls controlsList="nodownload"><source src="https://anonymous757575.github.io/diffariff-companion/audios/sample.wav" type="audio/wav"> Your Browser does not support the audio tag </audio> </td>
    <td class="tg-0pky">"Example Prompt"</td>
    <td class="tg-0lax"> <audio controls controlsList="nodownload"><source src="https://anonymous757575.github.io/diffariff-companion/audios/sample.wav" type="audio/wav"> Your Browser does not support the audio tag </audio> </td>
    <td class="tg-0pky"> <audio controls controlsList="nodownload"><source src="https://anonymous757575.github.io/diffariff-companion/audios/sample.wav" type="audio/wav"> Your Browser does not support the audio tag </audio> </td>
    <td class="tg-0pky"> <audio controls controlsList="nodownload"><source src="https://anonymous757575.github.io/diffariff-companion/audios/sample.wav" type="audio/wav"> Your Browser does not support the audio tag </audio> </td>
  </tr>
  <tr>
    <td class="tg-0pky">"Example Prompt"</td>
    <td class="tg-0lax"> <audio controls controlsList="nodownload"><source src="https://anonymous757575.github.io/diffariff-companion/audios/sample.wav" type="audio/wav"> Your Browser does not support the audio tag </audio> </td>
    <td class="tg-0pky"> <audio controls controlsList="nodownload"><source src="https://anonymous757575.github.io/diffariff-companion/audios/sample.wav" type="audio/wav"> Your Browser does not support the audio tag </audio> </td>
    <td class="tg-0pky"> <audio controls controlsList="nodownload"><source src="https://anonymous757575.github.io/diffariff-companion/audios/sample.wav" type="audio/wav"> Your Browser does not support the audio tag </audio> </td>
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
    <td class="tg-0pky">"Example Prompt"</td>
    <td class="tg-0lax"> <audio controls controlsList="nodownload"><source src="https://anonymous757575.github.io/diffariff-companion/audios/sample.wav" type="audio/wav"> Your Browser does not support the audio tag </audio> </td>
    <td class="tg-0pky"> <audio controls controlsList="nodownload"><source src="https://anonymous757575.github.io/diffariff-companion/audios/sample.wav" type="audio/wav"> Your Browser does not support the audio tag </audio> </td>
    <td class="tg-0pky"> <audio controls controlsList="nodownload"><source src="https://anonymous757575.github.io/diffariff-companion/audios/sample.wav" type="audio/wav"> Your Browser does not support the audio tag </audio> </td>
  </tr>
  <tr>
    <td class="tg-0pky">"Example Prompt"</td>
    <td class="tg-0lax"> <audio controls controlsList="nodownload"><source src="https://anonymous757575.github.io/diffariff-companion/audios/sample.wav" type="audio/wav"> Your Browser does not support the audio tag </audio> </td>
    <td class="tg-0pky"> <audio controls controlsList="nodownload"><source src="https://anonymous757575.github.io/diffariff-companion/audios/sample.wav" type="audio/wav"> Your Browser does not support the audio tag </audio> </td>
    <td class="tg-0pky"> <audio controls controlsList="nodownload"><source src="https://anonymous757575.github.io/diffariff-companion/audios/sample.wav" type="audio/wav"> Your Browser does not support the audio tag </audio> </td>
  </tr>
  <tr>
    <td class="tg-0pky">"Example Prompt"</td>
    <td class="tg-0lax"> <audio controls controlsList="nodownload"><source src="https://anonymous757575.github.io/diffariff-companion/audios/sample.wav" type="audio/wav"> Your Browser does not support the audio tag </audio> </td>
    <td class="tg-0pky"> <audio controls controlsList="nodownload"><source src="https://anonymous757575.github.io/diffariff-companion/audios/sample.wav" type="audio/wav"> Your Browser does not support the audio tag </audio> </td>
    <td class="tg-0pky"> <audio controls controlsList="nodownload"><source src="https://anonymous757575.github.io/diffariff-companion/audios/sample.wav" type="audio/wav"> Your Browser does not support the audio tag </audio> </td>
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
    <td class="tg-0pky" rowspan="2"> <audio controls controlsList="nodownload"><source src="https://anonymous757575.github.io/diffariff-companion/audios/sample.wav" type="audio/wav"> Your Browser does not support the audio tag </audio> </td>
    <td class="tg-0pky">"Example Prompt"</td>
    <td class="tg-0lax"> <audio controls controlsList="nodownload"><source src="https://anonymous757575.github.io/diffariff-companion/audios/sample.wav" type="audio/wav"> Your Browser does not support the audio tag </audio> </td>
    <td class="tg-0pky"> <audio controls controlsList="nodownload"><source src="https://anonymous757575.github.io/diffariff-companion/audios/sample.wav" type="audio/wav"> Your Browser does not support the audio tag </audio> </td>
    <td class="tg-0pky"> <audio controls controlsList="nodownload"><source src="https://anonymous757575.github.io/diffariff-companion/audios/sample.wav" type="audio/wav"> Your Browser does not support the audio tag </audio> </td>
  </tr>
  <tr>
    <td class="tg-0pky">"Example Prompt"</td>
    <td class="tg-0lax"> <audio controls controlsList="nodownload"><source src="https://anonymous757575.github.io/diffariff-companion/audios/sample.wav" type="audio/wav"> Your Browser does not support the audio tag </audio> </td>
    <td class="tg-0pky"> <audio controls controlsList="nodownload"><source src="https://anonymous757575.github.io/diffariff-companion/audios/sample.wav" type="audio/wav"> Your Browser does not support the audio tag </audio> </td>
    <td class="tg-0pky"> <audio controls controlsList="nodownload"><source src="https://anonymous757575.github.io/diffariff-companion/audios/sample.wav" type="audio/wav"> Your Browser does not support the audio tag </audio> </td>
  </tr>
  <tr>
    <td class="tg-0pky" rowspan="2"> <audio controls controlsList="nodownload"><source src="https://anonymous757575.github.io/diffariff-companion/audios/sample.wav" type="audio/wav"> Your Browser does not support the audio tag </audio> </td>
    <td class="tg-0pky">"Example Prompt"</td>
    <td class="tg-0lax"> <audio controls controlsList="nodownload"><source src="https://anonymous757575.github.io/diffariff-companion/audios/sample.wav" type="audio/wav"> Your Browser does not support the audio tag </audio> </td>
    <td class="tg-0pky"> <audio controls controlsList="nodownload"><source src="https://anonymous757575.github.io/diffariff-companion/audios/sample.wav" type="audio/wav"> Your Browser does not support the audio tag </audio> </td>
    <td class="tg-0pky"> <audio controls controlsList="nodownload"><source src="https://anonymous757575.github.io/diffariff-companion/audios/sample.wav" type="audio/wav"> Your Browser does not support the audio tag </audio> </td>
  </tr>
  <tr>
    <td class="tg-0pky">"Example Prompt"</td>
    <td class="tg-0lax"> <audio controls controlsList="nodownload"><source src="https://anonymous757575.github.io/diffariff-companion/audios/sample.wav" type="audio/wav"> Your Browser does not support the audio tag </audio> </td>
    <td class="tg-0pky"> <audio controls controlsList="nodownload"><source src="https://anonymous757575.github.io/diffariff-companion/audios/sample.wav" type="audio/wav"> Your Browser does not support the audio tag </audio> </td>
    <td class="tg-0pky"> <audio controls controlsList="nodownload"><source src="https://anonymous757575.github.io/diffariff-companion/audios/sample.wav" type="audio/wav"> Your Browser does not support the audio tag </audio> </td>
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
    <td class="tg-0pky"> <audio controls controlsList="nodownload"><source src="https://anonymous757575.github.io/diffariff-companion/audios/sample.wav" type="audio/wav"> Your Browser does not support the audio tag </audio> </td>
    <td class="tg-0lax"> <audio controls controlsList="nodownload"><source src="https://anonymous757575.github.io/diffariff-companion/audios/sample.wav" type="audio/wav"> Your Browser does not support the audio tag </audio> </td>
    <td class="tg-0pky"> <audio controls controlsList="nodownload"><source src="https://anonymous757575.github.io/diffariff-companion/audios/sample.wav" type="audio/wav"> Your Browser does not support the audio tag </audio> </td>
    <td class="tg-0pky"> <audio controls controlsList="nodownload"><source src="https://anonymous757575.github.io/diffariff-companion/audios/sample.wav" type="audio/wav"> Your Browser does not support the audio tag </audio> </td>
  </tr>
  <tr>
    <td class="tg-0pky"> <audio controls controlsList="nodownload"><source src="https://anonymous757575.github.io/diffariff-companion/audios/sample.wav" type="audio/wav"> Your Browser does not support the audio tag </audio> </td>
    <td class="tg-0lax"> <audio controls controlsList="nodownload"><source src="https://anonymous757575.github.io/diffariff-companion/audios/sample.wav" type="audio/wav"> Your Browser does not support the audio tag </audio> </td>
    <td class="tg-0pky"> <audio controls controlsList="nodownload"><source src="https://anonymous757575.github.io/diffariff-companion/audios/sample.wav" type="audio/wav"> Your Browser does not support the audio tag </audio> </td>
    <td class="tg-0pky"> <audio controls controlsList="nodownload"><source src="https://anonymous757575.github.io/diffariff-companion/audios/sample.wav" type="audio/wav"> Your Browser does not support the audio tag </audio> </td>
  </tr>
  <tr>
    <td class="tg-0pky"> <audio controls controlsList="nodownload"><source src="https://anonymous757575.github.io/diffariff-companion/audios/sample.wav" type="audio/wav"> Your Browser does not support the audio tag </audio> </td>
    <td class="tg-0lax"> <audio controls controlsList="nodownload"><source src="https://anonymous757575.github.io/diffariff-companion/audios/sample.wav" type="audio/wav"> Your Browser does not support the audio tag </audio> </td>
    <td class="tg-0pky"> <audio controls controlsList="nodownload"><source src="https://anonymous757575.github.io/diffariff-companion/audios/sample.wav" type="audio/wav"> Your Browser does not support the audio tag </audio> </td>
    <td class="tg-0pky"> <audio controls controlsList="nodownload"><source src="https://anonymous757575.github.io/diffariff-companion/audios/sample.wav" type="audio/wav"> Your Browser does not support the audio tag </audio> </td>
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

## User Study Sample Questions
Here, you can find examples of the questions participants had to answer in our user studies. The user studies were conducted using the GoListen online platform [[1](#references)]. Citation will be added in the camera-ready version.

### Audio Quality Assessment 

### Subjective Audio Prompt Adherence


## References
[1] *Barry, Dan, et al. "Go Listen: An End-to-End Online Listening Test Platform." Journal of Open Research Software 9.1 (2021)*