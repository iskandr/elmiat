# elmiat: Electronic Lady Macbeth In A Tree 

Embodied conversational agent placed inside a tree sculpture within an activated art space. 

## High level design 
### v0
Do this in real time: **ASR** -> **LLM** -> **TTS**

### v1


Instruction tuning of the core LLM using scripts with one or more rounds of interaction in this format: 

```
See: <emoji sequence describing camera input or dream imagery>
Hear: <ASR text transcription if awake>
Env: <is it dawn, dusk, day, or night? what is the position of the moon? is it low/flood/high/ebb tide?>
-->
Thought: <English language sequence in response to sensory inputs>
--> 
Speak: <optional speech sequence>
```

The model stays in a dream loop, being prompted by random imagery + current `Env` information at regular intervals. If someone approaches it also wakes up, added **ASR** transcription as a sensory input and use **TTS** for spoken outputs. 

## Questions

**ASR**
* Will generated speech be mis-interpreted by the ASR stage as new input?
* How to handle interruptions?
* Can multiple speakers be split into parallel text streams?

**LLM**
* Existing models get instruction-tuned to a very boring and general mode of discourse, should we try PEFT on them for a better style of conversation or do our own instruction tuning?
* Should we focus the base models on relevant text (Shakespeare, Everglades, ecology, sci-fi, mysticism, &c) before instruction tuning?
* What would *our* instruction tuning corpus look like?
* Should we include auxiliary information to the prompt such as time of day, location of sun and moon relative to the installed location, tides and other natural cycles? If so, how do we *also* capture the expected use of this information during instruction tuning?

**TTS** 
* What does Lady Macbeth In A Tree *sound* like?
* Which model should we use?
* How do we explore the space of voice embeddings?
* Can we make something that combines natural non-human sounds which is close enough to existing speaker embeddings to be understood by listeners?

**Beyond**
* Should we give the system a camera? If so, would we summarize the current visual scence via an image to text model and add that to the prompt?
* Are all interactions just concatenated up to the context size limit? Can we achieve longer-term memory via summarization of contexts at checkpoints?

