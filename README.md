# YouTube Clone

This project is a simplified version of YouTube, designed to provide a streamlined video-sharing experience. Users can browse, upload, and view videos while interacting with other core features typically found in a video-sharing platform. The application leverages serverless and cloud-native technologies to handle video processing, storage, and metadata.

## Table of Contents

- [Features](#features)
- [Demo](#demo)
- [Tech Stack](#tech-stack)
- [Architecture](#architecture)
- [Getting Started](#getting-started)
- [Project Structure](#project-structure)
- [Contributing](#contributing)
- [License](#license)

## Features

- **Video Browsing**: Users can explore a library of videos through search or category filters.
- **Video Playback**: Videos are streamed directly to the client through a smooth playback interface.
- **User Authentication**: Firebase Auth enables secure account registration and login.
- **Video Upload and Processing**: Uploaded videos are transcoded for optimized playback.
- **Commenting and Liking**: Users can interact with videos by adding comments or likes.
- **Responsive UI**: The application is designed to be accessible on both mobile and desktop screens.

## Demo

For privacy and content moderation reasons, this project is not currently hosted publicly. However, users who set up a local version can experience:

1. **Video Library**: View a list of uploaded videos.
2. **Video Streaming**: Play any video available in the library.
3. **Account Management**: Sign in or register via Firebase Auth.
4. **Upload Videos**: Add new video content for processing and playback.
5. **View Transcoded Videos**: Watch videos after they’ve been processed for playback quality.

## Tech Stack

- **Frontend**: Built with TypeScript and Next.js for server-rendered pages and optimized performance.
- **Backend**: Express.js and Docker manage server functionality.
- **Video Processing**: FFmpeg handles video transcoding.
- **Authentication**: Firebase Auth provides secure user accounts.
- **Database**: Metadata is stored in Firebase Firestore.
- **Storage**: Google Cloud Storage stores raw and transcoded video files.
- **Messaging & Orchestration**: Google Cloud Pub/Sub manages the video processing queue.
- **Hosting**: Google Cloud Run serves the web client and backend service.

## Architecture

This application is built with a serverless and containerized architecture, leveraging Google Cloud services to create a reliable, scalable platform:

1. **Google Cloud Storage** is used to store video files, with raw files uploaded directly and transcoded files added after processing.
2. **Google Cloud Pub/Sub** facilitates the flow of events between services, triggering the video processing pipeline.
3. **Cloud Run** hosts a private service that performs video transcoding using FFmpeg and uploads the processed video back to Cloud Storage.
4. **Firebase Firestore** stores video metadata, such as titles, descriptions, and user details.
5. **Cloud Run** also hosts the **Next.js** application, which serves as the web client and allows users to upload, browse, and watch videos.
6. **Firebase Functions** serve as an API layer for the Next.js app to securely interact with Firestore, retrieving video details and metadata for client display.

This setup balances cloud-native capabilities with serverless efficiency to handle dynamic workloads, especially during video upload and processing.

## Getting Started

To run this project locally:

### Prerequisites

- Node.js and npm
- Docker
- FFmpeg

### Installation

1. **Clone the Repository**:
   ```bash
   git clone https://github.com/yourusername/youtube-clone.git
   cd youtube-clone
   ```

2. **Install Dependencies**:
   ```bash
   npm install
   ```

3. **Set Up Environment Variables**:
   Create a `.env` file with required API keys and configurations, including Firebase, Google Cloud Storage, and Pub/Sub credentials.

4. **Run Docker Containers**:
   ```bash
   docker-compose up
   ```

5. **Start the Development Server**:
   ```bash
   npm run dev
   ```

   The application should now be accessible at `http://localhost:3000`.
