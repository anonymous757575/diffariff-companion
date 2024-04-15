<style>
audio{
  width:150px;
  height:40px;
}
audio::-webkit-media-controls-timeline,
audio::-webkit-media-controls-seek-back-button,
audio::-webkit-media-controls-seek-forward-button {
  display: none !important;
}

</style>


# Hello World


This is the accompanying website to "Diff-a-Riff: Musical Accompaniment Co-creation via Latent Diffusion Models" submitted to ISMIR 2024.

This website is a work in progress that will be completed by April 17th.



## User study sample questions
Here, you can find examples of the questions participants had to answer in our user studies.

### Audio Quality Assessment 

### Subjective Audio Prompt Adherence




## Sound examples
In this section, we demonstrate the generation abilities of our model under different conditioning signals.

### Context-based control
Given an existing piece of music, Diff-A-Riff allows the generation of various accompaniments. Here, we present various context music pieces and accompaniments generated conditioned on this context only.

<table class="tg">
<thead>
  <tr>
    <th class="tg-0pky">Reference</th>
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



### Text-based control


#### With context
Given a context music piece, Diff-A-Riff allows the generation of accompaniments based on a text prompt. Here, we present various context music pieces and various text-based accompaniments.


<table class="tg">
<thead>
  <tr>
    <th class="tg-0pky">Reference</th>
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


### Audio-based control

#### With context
Given a context music piece, Diff-A-Riff allows the generation of accompaniments based on an audio reference. Here, we present various context music pieces and various audio-based accompaniments.

#### Without context 
Diff-A-Riff also allows the generation of solo instrument tracks conditioned on audio only.



### Bonus

#### Interpolations

#### Variations

#### Loop Sampling

#### Stereo width


