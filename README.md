# whisper-longform

This is a repo for evaluating whisper for longform audio and indic languages

## Ways to improve performance

1. Try prompt ids which are contextual to the call
2. Force the model to return timestamps
3. Remove silences from the audio. If there are long pauses in the audio, they can make the model hallucinate and output gibberish. One solution is to trim the silences from the audio. This problem is specially prevalent if the silences are in start or end of the audio.
4. Add forced decoder IDs. This means, that we should force the model to either transcribe or translate to a specific language. I have seen performance boost with this method.
5. Add beam search. This is subjective, it will increase the time to inference and the memory footprint, but can help with better transcription.
6. Convert model to better transformer (for faster inference)
7. Variable chunk length. Usually it is best to keep it at 30s
8. If non of the above works, you can finetune the model using PEFT.

All of these parameters are availble in huggingface implementation of Whisper and I have added a notebook to try these out

## Where to go from here?

Here are some references to deepen your knowledge about Whisper and how to improve it's performance.

1. [Whisper finetuning guide (Kaggle)](https://www.kaggle.com/code/nbroad/whisper-training-starter-kit)
2. [Whisper finetuning guide (HF)](https://huggingface.co/blog/fine-tune-whisper)
3. [Whisper PEFT finetuning guide](https://github.com/Vaibhavs10/fast-whisper-finetuning#evaluation-metrics)

There are also some finetuned whisper models available on Indic languages, but they usually transcribe to Hindi itself. You will need to use another translation model to finally convert it to English (if your usecase is such) 
