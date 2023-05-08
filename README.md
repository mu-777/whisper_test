# Whisper test

## Prepare
- ```
  docker compose build
  ```

## Run
- ```
  MP3_PATH=<your mp3 path>
  docker compose run --rm -v $MP3_PATH:$MP3_PATH whisper \
    whisper $MP3_PATH --language ja --model large --output_dir ./
  ```

## Ref
- https://zenn.dev/gyabi/articles/3d2b3fb4e5bf23
- https://zenn.dev/kento1109/articles/d7d8f512802935