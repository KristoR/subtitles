# subtitles
Transcribing and translating subtitles using Google Colab, OpenAI API and Whisper.

### Getting started

The following should be done before running this notebook:
1. Create an API key on https://platform.openai.com/
2. Save the API key as a secret named `oai` on Google Colab. Make sure the notebook has access to the secret.
3. Mount Drive (Files->Mount Drive) on Google Colab.
4. Modify parameters for correct file location and context.
5. Execute the notebook (use GPUs).

### Parameters
Some of the parameters in the first code cell need modification. Feel free to modify them as you like.  
Probably only the following three should be changed each episode: `episode_path`, `extra_context`, `guest_context`

* Path
    * `episode_path` - this is a unique "folder" for this episode. 
    * `drive_path` - this is the root path to where the episodes are located
    * `audiofile_name` - this is the name of the audiofile
    * `initial_subtitles_name` - initial transcription from Whisper
    * `corrected_subtitles_name` - GPT corrected transcription
    * `translated_subtitles_name` - GPT translated transcription
* Context
    * `extra_context` - topics and keywords used in the podcast
    * `guest_context` - name and background of the guest
    * `background_context` - general background about the podcast, hosts, etc
* Other
    * `batch_size` - default 100, larger number = more context (better result) but might hit API limits. This is basically subtitles' line count per prompt.
    * `language` - 2-letter code for original language, e.g. `et`
    * `language_full` - full name of original language, e.g. `Estonian`
    * `whisper_model` - the Whisper model to use
    * `openai_model` - the OpenAI model to use
    

####  Path example. 
Your episodes are on Google Drive under folder "my_podcast" (`/content/drive/MyDrive/my_podcast`).  
You name each episode with date as `YYYYMMDD`, e.g. `20250420`. Your audiofile is always called `audio.mp3`. I.e., when checking on Google Drive, you find the file under `my_podcast/20250420/audio.mp3`. 
Then, the parameters should be as follows: 
* `drive_path` = "/content/drive/MyDrive/my_podcast"
* `episode_path` = "20250420"
* `audiofile_name` = "audio.mp3"

The subtitles are added to the same folder.

#### 