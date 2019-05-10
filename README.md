# What does stream-forwarder do?
Stream-forwarder allows you to forward an incoming rtmp stream to multiple rtmp destinations via a simple Docker container.
This allows you to multi-stream to multiple platforms simultaneously.

# How to use stream-forwarder

## Modifying stream destinations
Alter the `nginx.conf.add` config file by adding a `push rtmp://<HOST_HERE>/<STREAM_KEY_HERE>;` line under 'application live'.
Two destinations, one for YouTube and another one for Facebook, have already been added as an example, just insert the stream key you get when creating a new live stream on YouTube or Facebook.

⚠️ **Encrypted streams over rtmps are not supported. Disable this option when creating a Facebook live stream.**

## Building the stream forwarder
`docker build . -t stream-forwarder`

## Running the stream forwarder
`docker run -p 1935:1935 stream-forwarder`

## Enter the following settings in OBS Studio
Under Settings > Stream:
- **Service:** `Custom`
- **Server:** `rtmp://<YOUR_SERVER_IP>/live`, or `rtmp://127.0.0.1/live` when running the stream-forwarder container locally
- **Stream Key:** `test`
- Leave 'Use authentication' unchecked

## Preview stream in VLC media player
Open the following network stream: `rtmp://<YOUR_SERVER_IP>/live/test`, or `rtmp://127.0.0.1/live` when running the stream-forwarder container locally.

