# 102103058-Mashup
A Flask application that provides an API endpoint `/generate_mashup` for generating music mashups from YouTube videos and sending them via email. Here's a brief overview of what the code does:

1. **Flask Application Setup**: Initializes a Flask application instance.

2. **generate_mashup Endpoint**: Handles POST requests to `/generate_mashup` route. It expects a JSON payload containing information about the singer, the number of videos to download (`n`), the duration of each segment in seconds, and the email address to send the mashup to. It performs the following steps:
   - Validates the input parameters (`n` and duration) and returns an error if they are less than or equal to 10 and 20 respectively.
   - Creates a directory named `downloads` if it doesn't exist already.
   - Downloads videos from YouTube based on the provided singer name using `yt_dlp`.
   - Converts downloaded videos into audio files using `moviepy`.
   - Cuts the audio files into segments of the specified duration using `moviepy`.
   - Merges the segmented audio files into a single audio file.
   - Creates a zip file containing the mashup audio file.
   - Sends an email with the zip file attachment using `yagmail`.
   - Cleans up by deleting the `downloads` directory.

3. **Utility Functions**: 
   - `download_videos`: Downloads videos from YouTube based on the provided singer name.
   - `convert_to_audio`: Converts video files into audio files.
   - `cut_audio`: Cuts audio files into segments.
   - `merge_audios`: Merges multiple audio files into a single audio file.
   - `clean_up`: Deletes the `downloads` directory to clean up the generated files.

4. **Main Block**: Runs the Flask application in debug mode if the script is executed directly.

Overall, this script provides a simple API for generating music mashups from YouTube videos and sending them via email.
