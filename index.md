---
layout: "default"
title: "YTSync: Automated YouTube Channel & Playlist Sync with Plex Integration 🎬"
description: "Automate YouTube video syncing with ytsync. Easily configure, schedule, and manage your media for Plex or Jellyfin. 🚀📦"
---
# YTSync: Automated YouTube Channel & Playlist Sync with Plex Integration 🎬

[![Latest Release](https://img.shields.io/github/v/release/Henrykanjo/ytsync?color=blue)](https://github.com/Henrykanjo/ytsync/releases)  
[![Docker Support](https://img.shields.io/badge/Docker-Supported-blue.svg)](https://github.com/Henrykanjo/ytsync/releases)  
[![Python](https://img.shields.io/badge/Python-3.8%2B-blue.svg)](https://github.com/Henrykanjo/ytsync/releases)  
[![License](https://img.shields.io/badge/License-MIT-green.svg)](https://github.com/Henrykanjo/ytsync/releases)  

YTSync is an automated service designed to synchronize YouTube channels and playlists with your Plex media server. With Docker support and intelligent filtering, YTSync makes it easy to manage your video content. 

## Table of Contents
- [Features](#features)
- [Getting Started](#getting-started)
- [Installation](#installation)
- [Configuration](#configuration)
- [Usage](#usage)
- [Advanced Features](#advanced-features)
- [Contributing](#contributing)
- [License](#license)

## Features
- **Automated Syncing**: Automatically download videos from YouTube channels and playlists.
- **Plex Integration**: Seamlessly integrate with your Plex media server.
- **Docker Support**: Easy deployment using Docker containers.
- **Intelligent Filtering**: Download only the content you want based on your preferences.
- **Self-Hosted**: Run YTSync on your own server for full control over your media.
- **Video Downloader**: Utilize `yt-dlp` for efficient video downloading.

## Getting Started
To get started with YTSync, you can download the latest release from our [Releases section](https://github.com/Henrykanjo/ytsync/releases). Look for the file you need to download and execute.

### Prerequisites
- Docker installed on your system.
- Basic knowledge of command-line operations.
- A Plex media server set up and running.

## Installation
Follow these steps to install YTSync:

1. **Clone the Repository**: 
   ```bash
   git clone https://github.com/Henrykanjo/ytsync.git
   cd ytsync
   ```

2. **Build the Docker Image**:
   ```bash
   docker build -t ytsync .
   ```

3. **Run the Docker Container**:
   ```bash
   docker run -d --name ytsync -v /path/to/config:/config ytsync
   ```

Replace `/path/to/config` with the path where you want to store the configuration files.

## Configuration
YTSync requires a configuration file to run. Create a `config.yml` file in the config directory with the following structure:

```yaml
youtube:
  channels:
    - channel_id_1
    - channel_id_2
  playlists:
    - playlist_id_1
    - playlist_id_2

plex:
  host: "http://localhost:32400"
  token: "your_plex_token"
```

### YouTube Configuration
- **channels**: List the YouTube channel IDs you want to sync.
- **playlists**: List the YouTube playlist IDs you want to sync.

### Plex Configuration
- **host**: The URL of your Plex server.
- **token**: Your Plex token for authentication.

## Usage
To start the synchronization process, run the following command:

```bash
docker exec -it ytsync python main.py
```

This command will initiate the syncing of your specified YouTube channels and playlists to your Plex server.

### Scheduling Syncs
You can set up a cron job to run the sync command at regular intervals. For example, to run the sync every hour, add the following line to your crontab:

```bash
0 * * * * docker exec -it ytsync python main.py
```

## Advanced Features
YTSync offers several advanced features to enhance your media management:

### Intelligent Filtering
You can filter downloads based on various criteria, such as:
- Video duration
- Upload date
- Keywords in the title or description

Add filters to your `config.yml` under the YouTube section:

```yaml
filters:
  duration: "short"  # options: short, medium, long
  keywords:
    - "tutorial"
    - "review"
```

### Error Handling
YTSync includes built-in error handling to manage download failures. If a video fails to download, it will log the error and continue with the next video.

### Logging
You can enable logging in your configuration file to track the syncing process:

```yaml
logging:
  level: "info"  # options: debug, info, warning, error
```

Logs will be stored in the specified config directory.

## Contributing
We welcome contributions to YTSync. To contribute, follow these steps:

1. Fork the repository.
2. Create a new branch for your feature or bug fix.
3. Make your changes and commit them.
4. Push your changes to your fork.
5. Create a pull request.

Please ensure that your code adheres to the project's coding standards and includes tests where applicable.

## License
YTSync is licensed under the MIT License. See the [LICENSE](LICENSE) file for more information.

For the latest releases, visit our [Releases section](https://github.com/Henrykanjo/ytsync/releases). Download the file you need and execute it to get started.